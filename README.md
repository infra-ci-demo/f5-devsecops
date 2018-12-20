# デモ環境

```
mkdir ~/temp && cd ~/temp
git clone https://github.com/infra-ci-demo/f5-devsecops.git

docker run -d -p 8888:8888 --name aitac -e PASSWORD=password \
           -v ~/temp/f5-devsecops:/notebooks/f5-devsecops \
           irixjp/aitac-automation-jupyter
```

1. コンテナを起動したらブラウザで `localhost:8888` へアクセス
1. パスワードは `PASSWORD=password` で設定した文字列
1. ログイン後、 `f5-devsecops` へ移動し、`setup.ipynb` を起動する

