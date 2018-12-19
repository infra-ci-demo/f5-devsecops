# デモ環境

## 要件

1. Ansible 2.7.x 以上
1. CentOS7.x (最新版推奨)
1. インターネット接続環境

## 共通

```
mkdir ~/temp && cd ~/temp
git clone https://github.com/infra-ci-demo/f5-devsecops.git
cd f5-devsecops
```

## GitLab CI環境の構築

```
vim inv_gitlab.yml
```

以下を必要に応じて編集
```
   ansible_host: 10.208.81.221       ← GitLabを起動するサーバーのIPアドレス
   ansible_user: centos              ← sudo 可能なユーザー（もしくはroot）
   ansible_ssh_pass: redhat          ← 接続パスワード。鍵認証を使う場合は行ごと削除する
   gitlab_root_password: password    ← GitLabの管理者パスワード(複雑なものへ変更する)
   gitlab_runner_token: token-AABBCC ← GitLabが内部で使うトークン(複雑なものへ変更する)
```


セットアップを実行（5～15分程度）
```
ansible-playbook -i inv_gitlab.yml start_gitlab.yml
```

終了したらブラウザで`http://{{ ansible_host }}:8080` へアクセスし、`root/設定したパスワード`でログインする。

ログイン後の動作確認は以下で実施

1. New Project → Import project → Repo by URL → Git repository URL `https://github.com/infra-ci-demo/f5-devsecops.git` を入力して Create project
1. インポートが終了したら、CI / CD → Pipelines → Run Pipelines → Create pipeline
1. パイプラインが正常終了すればセットアップは成功


