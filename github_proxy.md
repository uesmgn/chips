

### Githubのプロキシ設定

git config --add http.proxy [YOUR_PROXY_SETTING]

git config --global --add credential.github.com.httpproxy [YOUR_PROXY_SETTING]



### Githubのプロキシ設定を解除

git config -- unset http.proxy

git config --global --unset credential.github.com.httpproxy


