# ROS2 メモ

## パラメータを確認する
  ```bash
  ros2 param dump /my_node
  ```

## トピックの接続状況を確認する

  ```bash
  ros2 topic info --verbose /topic
  ```

## nav2 をビルドする
  ```bash
  colcon build --symlink-install --cmake-args -DBUILD_TESTING=OFF
  ```