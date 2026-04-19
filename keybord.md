# keyd 設定メモ

`CapsLock` をナビゲーションレイヤーとして使うための `keyd` セットアップ手順。

## 1. `keyd` をインストール

```bash
sudo add-apt-repository ppa:keyd-team/ppa
sudo apt update
sudo apt install keyd
```

## 2. `keyd` を起動

```bash
sudo systemctl enable --now keyd
```

## 3. 設定ファイルを編集

```bash
sudo vi /etc/keyd/default.conf
```

設定例:

```ini
[ids]
*

[main]
capslock = layer(nav)

[nav]
b = left
f = right
p = up
n = down
a = home
e = end
h = backspace
d = delete
```

## 4. `keyd` を再起動

```bash
sudo systemctl restart keyd
```
