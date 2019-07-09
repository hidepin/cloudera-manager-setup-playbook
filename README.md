common-ansible-role
============================================================

# 概要

OS初期インストール時の共通設定。
設定変更したファイルと変更前のファイルをバックアップを取得。
設定変更後再起動を実行。

## 共通設定

1. 必要パッケージのインストール (6系を最小構成でインストールした場合にシナリオ実行に必要なパッケージ)
2. selinuxの無効化 (要再起動)
3. hostsファイルの設定 (同時に設定したhostを設定)
4. yum proxy設定 (proxyサーバを指定した場合に設定)
5. DNSの無効化 (nameserverを設定していない場合に実施)
6. ユーザを作成
7. パッケージの最新化

## RHEL6/CentOS6設定

1. networkの追加設定
  - NOZEROCONFの設定
  - ipv6設定の無効化
  - NetworkManagerの無効化
2. OS環境追加設定
  - coreのサイズをulimit化
3. firewallの無効化
4. ntpの設定

## RHEL7/CentOS7設定/Fedora25

1. rhel subscription設定 (rhel_subscription設定時に実施)
2. runlebelをmulti-user.targetに設定
3. firewallの無効化
4. 仮想bridgeの無効化
5. chrony設定
6. journaldの永続化設定
7. rsyslog設定 (Fedora25以外)
8. abrt設定
9. kdump設定 (要再起動)
10. limits設定
11. tuned設定

# 動作確認済み環境

- RHEL6 (見直し中)
- RHEL7
- CentOS6 (見直し中)
- CentOS7
- Fedora25

# 設定

- proxy_env.no_proxy         # proxyサーバを設定した場合、proxyサーバを経由しない通信相手を指定
- proxy_env.http_proxy       # httpのproxyサーバを使用する場合指定
- proxy_env_https_proxy      # httpのproxyサーバを使用する場合指定
- rhel_subscription.username # rhelのsubscription設定する場合に指定 (rhel_subscriptionを設定していれば、省略時シナリオ実行時に入力することになる)
- rhel_subscription.password # rhelのsubscription設定する場合に指定 (rhel_subscriptionを設定していれば、省略時シナリオ実行時に入力することになる)
- ntp_server                 # ntpサーバ
- rhel_subscription_enabled  # RHELでサブスクリプションを登録するかどうかを指定
- grub_cfg_uefi              # UEFIモードでgrub2-mkconfigで指定するパスを指定
- grub_cfg_legacy            # BIOSモードでgrub2-mkconfigで指定するパスを指定
- kdump_partition            # kdumpのvmcoreを出力するパーティションを指定
- kdump_path:                # vmcoreを出力するパーティションからのパスを指定
- common_user.name           # 作成するユーザ名
- common_user.passsword      # 作成するユーザのパスワード(ハッシュ値)
- common_user.uid            # 作成するユーザのuid
- common_user.group          # 作成するユーザのgroup名
- common_user.gid            # 作成するユーザのgid
- limits_setting             # /etc/security/limits.confを設定
- tuned_profile              # activeにするtuned profile名を設定
- tuned_profile_parameter    # tunedの設定
- force_install_pkg          # インストール済みであっても強制インストールするパッケージリスト(kernel等)
- update_pkg_enabled         # update_pkgをアップデートするかどうかを指定
- update_pkg                 # アップデートするパッケージ一覧

# 依存関係

依存するroleはありません

# TODO

  - RHEL6/CentOS6の見直し
