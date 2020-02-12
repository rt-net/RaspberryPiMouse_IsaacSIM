# RaspberryPiMouse_IsaacSIM

![raspimouse_isaac_sim](https://github.com/rt-net/RaspberryPiMouse_IsaacSIM/blob/images/images/raspimouse_isaac_sim.png "raspimouse_isaac_sim")

Raspberry Pi MouseをIsaac Sim上でシミュレーションするためのIsaacパッケージです。  
本パッケージはブログ記事[Isaac SIMで走るRasPiMouse[1] – セットアップ編](https://www.rt-shop.jp/blog/archives/11427)に際して作成されたものです。記事本編もぜひご覧ください。

## Requirements
本パッケージは下記環境で動作確認ができています。

* OS: Ubuntu 18.04.2 LTS
* Isaac SDK: 2019.2
* Isaac Sim: 2019.2

## Installation
* [Isaac SDK](https://docs.nvidia.com/isaac/isaac/doc/setup.htm)、[Isaac Sim](https://docs.nvidia.com/isaac/isaac_sim/setup.html)をインストールします。
  * インストール手順については[Isaac SIMで走るRasPiMouse[1] – セットアップ編](https://www.rt-shop.jp/blog/archives/11427)もぜひご参照ください。
* 本パッケージをダウンロードします。

  ```
  $ cd ~/isaac/apps
  $ git clone https://github.com/rt-net/RaspberryPiMouse_IsaacSIM.git
  ```

* URDFモデルをコピーします。

  ```
  $ cd RaspberryPiMouse_IsaacSIM
  $ cp -r raspimouse_description ~/UnrealEngine/IsaacSimProject/Content/URDF
  ```

* JSONファイルを編集します。ユーザー名等使用する環境に適宜合わせてください。

  ```
  $ vim bridge_config/raspimouse_full.json
  ```

* 下記のようにraspimouse_full_graph.jsonとraspimouse_full_config.jsonのパスを記入します。[username]の部分を使用しているユーザー名に置き換えてください。

  ```
  {
      "graphs": ["/home/[username]/isaac/apps/RaspberryPiMouse_IsaacSIM/bridge_config/raspimouse_full_graph.json"],
      "configs": ["/home/[username]/isaac/apps/RaspberryPiMouse_IsaacSIM/bridge_config/raspimouse_full_config.json"]
  }
  ```

## Usage
* 下記コマンドでUnreal Engineを起動し、シミュレータを実行します。

  ```
  $ ~/UnrealEngine/Engine/Binaries/Linux/UE4Editor IsaacSimProject FlatMap -vulkan -isaac_sim_config_json="$HOME/isaac/apps/RaspberryPiMouse_IsaacSIM/bridge_config/raspimouse_full.json"
  ```

* 下記コマンドでジョイスティック操作するパッケージを起動します。

  ```
  $ cd ~/isaac
  $ bazel run apps/RaspberryPiMouse_IsaacSIM:joystick
  ```

## License
This repository is licensed under the MIT license, see [LICENSE](./LICENSE).
