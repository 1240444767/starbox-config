# starmusic-config

星音乐（StarMusic）的**远程配置分发仓库**（原 starbox-config，已改名对齐应用名）。

| 文件 | 说明 |
| --- | --- |
| `index.json` | 客户端远程配置（Base64 + RC4 加密，解密后为 `{ "data": { maintain, config, notice, update_log, group, task, update, about } }`） |
| `xy.txt` | 用户协议 / 免责声明 / 隐私政策（明文，客户端直接展示） |

## 客户端取用地址

```
https://1240444767.github.io/starmusic-config/index.json
https://cdn.jsdelivr.net/gh/1240444767/starmusic-config@main/index.json
https://gh-proxy.com/https://raw.githubusercontent.com/1240444767/starmusic-config/main/index.json
```

三条线路由客户端按顺序回退，任一条可用即可；全部失败时客户端改用 APK 内置的 `assets/default_config.json` 兜底。

## 更新配置

1. 改本地明文配置；
2. 用与客户端一致的密钥做 RC4 加密后 Base64 编码，覆盖 `index.json`；
3. commit & push，客户端下次启动生效（Pages 缓存约 10 分钟，jsDelivr 约 1 天）。

> 明文配置不要提交进任何仓库。