cloudera-manager-setup-playbook
============================================================

# 概要

Cloudera Managerをインストールする事前状態に設定。
/root/cloudera-manager-installer.binにインストーラーを配置

# Cloudera Managerのインストール手順

1. Cloudera Managerのホストにログインしrootになる。

  ```
  su -
  ```

2. Cloudera Managerのインストーラーを起動

  ```
  ./cloudera-manager-installer.bin
  ```

  1. Cloudera Managerのライセンスの同意

  2. OpenJDKのライセンスの同意

3. Cloudera Managerからセットアップ

  1. Cloudera Managerにアクセス http://(Cloudera Managerホスト):7180

  2. ログイン
    - ユーザ名: admin
    - パスワード: admin

  3. エンドユーザライセンスの同意

    「はい。エンドユーザーライセンスの契約条件に同意します」にチェックを入れ、「続行」を押下する

  4. エディションの選択

    「Cloudera Express」を選択し、「続行」を押下する

  5. 最終確認

    「続行」を押下する

  6. 選択肢に従いインストールする

# 動作確認済み環境

- RHEL7
- CentOS7

# 依存関係

- common-ansible-role

# TODO

  - RHEL6/CentOS6の見直し
