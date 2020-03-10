

### Githubのプロキシ設定

git config --add http.proxy http://proxy.nagaokaut,ac.jp:8080

git config --global --add credential.github.com.httpproxy http://proxy.nagaokaut,ac.jp:8080



### Githubのプロキシ設定を解除

git config -- unset http.proxy

git config --global --unset credential.github.com.httpproxy


