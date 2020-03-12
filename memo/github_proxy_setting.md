### Githubの設定を確認

```
> git config -l
> git config --global -l
```

### Githubのプロキシ設定

```
> git config --add http.proxy http://your_proxy_setting:8080
> git config --global --add credential.github.com.httpproxy http://your_proxy_setting:8080
```

### Githubのプロキシ設定を解除

```
> git config -- unset http.proxy
> git config --global --unset credential.github.com.httpproxy
```
