# OSセットアップ

## Ubuntuのインストール

Ubuntuのインストールは、[Ubuntuのインストール](https://ubuntu.com/tutorials/install-ubuntu-server#1-overview)を参照してください。

## MicroK8sのインストール

次にMicroK8sをインストールします。

MicroK8sとは、Ubuntuのパッケージ管理システムであるSnapを用いてインストールすることができるKubernetesのディストリビューションです。

Kubernetesについては、[Kubernetesドキュメント](https://kubernetes.io/ja/docs/home/)を参照してください。

```bash
$ sudo snap install microk8s --classic --channel=1.28
```

最新のMicroK8sのインストールは、[MicroK8sのインストール](https://microk8s.io/docs/getting-started)を参照してください。

### MicroK8sの設定

MicroK8sにCoreDNSを設定します。

CoreDNSとは、KubernetesのDNSサーバーです。Kubernetesでは、PodのIPアドレスは動的に割り当てられるため、PodのIPアドレスを直接指定することはできません。そのため、PodのIPアドレスを名前で指定することができるようにDNSサーバーを設定する必要があります。

```bash
$ sudo microk8s.enable dns
```

今後、MicroK8s上のリソースを操作する際は、次のコマンドを実行してください。

```bash
$ sudo microk8s.kubectl <command>
```
