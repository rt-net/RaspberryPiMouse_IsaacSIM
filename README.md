# RaspberryPiMouse_IsaacSIM

Raspberry Pi MouseをIsaac Sim上でシミュレーションするためのIsaacパッケージです。

## Requirements
本パッケージは下記環境で動作確認ができています。

* OS: Ubuntu 18.04.2 LTS
* Isaac SDK: 2019.2
* Isaac Sim: 2019.2

## Installation
本パッケージをダウンロードします。

```
$ ~/isaac/apps
$ git clone https://github.com/rt-net/RaspberryPiMouse_IsaacSIM.git
```
URDFモデルをコピーします。
```
$ cd RaspberryPiMouse_IsaacSIM
$ cp -r raspimouse_description ~/UnrealEngine/IsaacSimProject/Content/URDF
```

JSONファイルを編集します。ユーザー名等使用する環境に適宜合わせてください。

```
$ vim bridge_config/raspimouse_full.json
```
下記のようにraspimouse_full_graph.jsonとraspimouse_full_config.jsonのパスを記入します。
```
{
    "graphs": ["/home/ubuntu/isaac/apps/RaspberryPiMouse_IsaacSIM/bridge_config/raspimouse_full_graph.json"],
    "configs": ["/home/ubuntu/isaac/apps/RaspberryPiMouse_IsaacSIM/bridge_config/raspimouse_full_config.json"]
}
```

## Usage
下記コマンドでUnreal Engineを起動し、シミュレータを実行します。

```
$ ~/UnrealEngine/Engine/Binaries/Linux/UE4Editor IsaacSimProject FlatMap -vulkan -isaac_sim_config_json="/home/ubuntu/isaac/apps/RaspberryPiMouse_IsaacSIM/bridge_config/raspimouse_full.json"
```

下記コマンドでジョイスティック操作するパッケージを起動します。

```
$ cd ~/isaac
$ bazel run apps/RaspberryPiMouse_IsaacSIM:joystick
```

## License
This repository is licensed under the MIT license, see [LICENSE](./LICENSE).
