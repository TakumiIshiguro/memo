# Docker Setup Memo (Ubuntu)

Docker Engine と NVIDIA Container Toolkit をインストールし、Docker コンテナから GPU を使えるようにする手順。

## 1. Docker Engine

### 古いバージョンを削除

```bash
sudo apt-get remove docker docker-engine docker.io containerd runc
```

### 必要なパッケージとリポジトリを登録

```bash
sudo apt-get update
sudo apt-get install -y ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```

```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

### Docker をインストール

```bash
sudo apt-get update
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

## 2. NVIDIA Container Toolkit (CDI)

### リポジトリを設定

```bash
curl -fsSL https://nvidia.github.io/libnvidia-container/gpgkey | sudo gpg --dearmor -o /usr/share/keyrings/nvidia-container-toolkit-keyring.gpg \
  && curl -s -L https://nvidia.github.io/libnvidia-container/stable/deb/nvidia-container-toolkit.list | \
    sed 's#deb https://#deb [signed-by=/usr/share/keyrings/nvidia-container-toolkit-keyring.gpg] https://#g' | \
    sudo tee /etc/apt/sources.list.d/nvidia-container-toolkit.list
```

### インストール

```bash
sudo apt-get update
sudo apt-get install -y nvidia-container-toolkit
```

### CDI スペックを生成

```bash
sudo nvidia-ctk cdi generate --output=/etc/cdi/nvidia.yaml
```

### Docker ランタイムとして設定して再起動

```bash
sudo nvidia-ctk runtime configure --runtime=docker
sudo systemctl restart docker
```

## 3. 仕上げ

### ユーザーを docker グループに追加

次回ログイン以降、`sudo` なしで `docker` コマンドを実行できるようになる。

```bash
sudo usermod -aG docker $USER
```

現在のシェルだけ設定を即時反映する。

```bash
newgrp docker
```

## 4. 動作確認

コンテナ内から GPU 情報が表示されれば完了。

```bash
docker run --rm --gpus all nvidia/cuda:12.0.0-base-ubuntu22.04 nvidia-smi
```
