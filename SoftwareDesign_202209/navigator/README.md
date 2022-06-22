# 環境構築

作業環境を準備する。

```
python -m venv sd202209
source sd202209/bin/activate
pip install -U pip
```

Ansible NavigatorとAnsibleをインストールする。

```
pip install ansible-navigator
pip install ansible
```

# Ansible Navigatorを利用する

作業用ディレクトリをチェックアウトする。

```
git clone -b SoftwareDesign_202209 https://github.com/saito-hideki/books
cd books/SoftwareDesign_202209
```

マネージドノード用のコンテナを起動する。

```
(cd environment && docker-compose up -d)
 docker ps
CONTAINER ID   IMAGE          COMMAND        CREATED         STATUS         PORTS     NAMES
6ac05db100de   sd202209_tgt   "/sbin/init"   6 seconds ago   Up 5 seconds             sd202209-tgt-3
7a81326ce596   sd202209_tgt   "/sbin/init"   6 seconds ago   Up 5 seconds             sd202209-tgt-2
34da1c83c263   sd202209_tgt   "/sbin/init"   6 seconds ago   Up 5 seconds             sd202209-tgt-1
```

Ansible Navigatorを使用してPlaybookを実行する。

```
cd navigator
ansible-navigator run -i inventory/hosts -m stdout playbook/ping.yml
```

Ansible Navigatorを使用してPlaybookの実行結果を確認する。

```
ansible-navigator replay artifacts/ping-artifact-2022-06-22T07:48:40.220493+00:00.json
```