# starbox-config

星盒 / 星音乐 系列应用的**远程配置分发仓库**。

| 文件 | 说明 |
| --- | --- |
| `index.json` | 客户端远程配置（Base64 + RC4 加密，解密后为 `{ "data": { maintain, config, notice, update_log, group, task, update, about } }`） |
| `xy.txt` | 用户协议 / 免责声明 / 隐私政策（明文，客户端直接展示） |

## 客户端取用地址

```
https://1240444767.github.io/starbox-config/index.json
https://cdn.jsdelivr.net/gh/1240444767/starbox-config@main/index.json
https://raw.githubusercontent.com/1240444767/starbox-config/main/index.json
```

三条线路由客户端按顺序回退，任一条可用即可。

## 更新配置

1. 改本地明文配置；
2. 用与客户端一致的密钥做 RC4 加密后 Base64 编码，覆盖 `index.json`；
3. commit & push，客户端下次启动生效。

> 明文配置不要提交进任何仓库。