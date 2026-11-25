# 项目可用额外磁盘存储

账号 `zilu.zhang` 在以下三个磁盘上均有可读写的个人目录，可在任一目录中存放项目文件。

| 挂载点 | 个人目录 | 磁盘可用空间（2026-11-18） |
| --- | --- | ---: |
| `/n7_ssd3` | `/n7_ssd3/users/zilu.zhang` | 约 3.5 TiB |
| `/n7_ssd4` | `/n7_ssd4/users/zilu.zhang` | 约 3.4 TiB |
| `/n8_ssd1` | `/n8_ssd1/users/zilu.zhang` | 约 3.4 TiB |

运行以下命令可查看这三个磁盘当前的剩余空间。

```bash
df -h /n7_ssd3 /n7_ssd4 /n8_ssd1
```
