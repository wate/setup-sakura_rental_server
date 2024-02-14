さくらのレンタルサーバー初期セットアップ
==================

さくらのレンタルサーバーの初期セットアップを行うことが出来ます。

前提条件/事前準備
------------------

- Ansibleがインストールされていること
    - [Installing Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)
- さくらのレンタルサーバーにSSHでログインできること
    - **ライトプランを利用している場合は利用できません。**
- SSH公開鍵認証の設定を行っていること
    - [SSH公開鍵認証の設定をしたい](https://help.sakura.ad.jp/rs/2804/)

利用方法(1)
------------------

### 単一のサーバーに適用する場合

以下のコマンドを実行してください。

環境変数「`SAKURA_LOGIN_PASSWORD`」にログインパスワードを設定後に以下のコマンドを実行してください。  
※`${SAKURA_FTP_SERVER}` は「さくらのレンタルサーバー」のFTPサーバー(初期ドメイン)を表しています。

```bash
ansible-playook setup.yml -i ${SAKURA_FTP_SERVER},
```

### 複数のサーバーに適用する場合

インベントリファイル(`hosts.yml`)に対象サーバーの情報を記述後、以下のコマンドを実行してください。
※インベントリファイルの記述方法については後述します。

```bash
ansible-playook setup.yml
```

インベントリファイルの記述方法
------------------

以下のサンプルを参考にインベントリファイル(`hosts.yml`)に対象サーバーの情報を記述してください。

### サンプル

```yaml
all:
  hosts:
    rolly.sakura.ne.jp:
      ansible_host: rolly.sakura.ne.jp
      ansible_user: rolly
      ansible_ssh_private_key_file: ~/.ssh/id_rsa
    pepper.sakura.ne.jp:
      ansible_host: pepper.sakura.ne.jp
      ansible_user: pepper
      ansible_ssh_private_key_file: ~/.ssh/id_rsa
    freckles.sakura.ne.jp:
      ansible_host: freckles.sakura.ne.jp
      ansible_user: freckles
      ansible_ssh_private_key_file: ~/.ssh/id_rsa
```

License
------------------

MIT License
