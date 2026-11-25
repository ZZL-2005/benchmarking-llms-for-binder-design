# 集群已有的蛋白质结构预测与设计模型

2026-11-18 以账号 `zilu.zhang` 核对。扫描覆盖 `n1` 至 `n8` 的 32 个 SSD 共享目录、8 个盘根 `models/` 目录及个人模型目录。下列权重均可读，本次盘点未运行 GPU 推理。

## 共享结构预测模型

ESMFold2 标准版在 `esm/`，Fast 版在 `esmf/`。两版各有 6 个 safetensors 分片，逐片核对了文件大小、张量名称和分片索引。表中大小均指磁盘上的权重文件。

| 模型 | 权重目录 | 已核实的文件或配置 |
| --- | --- | --- |
| ESMFold2 | `/n1_ssd1/share/models/esm/` | 6 个分片共 24.51 GiB。折叠主干 48 层，支持 MSA 输入。 |
| ESMFold2-Fast | `/n1_ssd1/share/models/esmf/` | 6 个分片共 24.34 GiB。折叠主干 24 层，使用单序列模式。 |
| AlphaFold 3 | `/n1_ssd1/share/AF3/model/` | `af3.bin.zst`（973.27 MiB）。有[原生启动脚本](/n1_ssd1/share/AF3/bin/run_native_af3.sh)和[已通过的 GPU 推理测试记录](/n1_ssd1/share/AF3/records/6000d_validation.json)。 |
| Boltz-2 | `/n1_ssd1/share/models/boltz/` | 结构预测权重 `boltz2_conf.ckpt` 和亲和力预测权重 `boltz2_aff.ckpt`。 |
| Protenix v2 | `/n1_ssd1/share/models/protenix/checkpoint/` | `protenix-v2.pt`（1.73 GiB）。`protenix_base_default_v2.0.0.pt` 指向同一文件。 |
| IntelliFold v2 | `/n1_ssd1/share/models/intellifold/` | 标准版 `intellifold_v2.bin.zst` 和 Flash 版 `intellifold_v2_flash.pt`。 |
| Mol-1 Base | `/n1_ssd1/share/models/mol1/checkpoint/` | `mol-1-base.pt`（2.23 GiB）。 |

共享 Python 环境位于 `/n1_ssd1/share/venvs/`。`fold/bin/python` 和 `mol1/bin/python` 对当前账号可执行。`esm/`、`ifv2/`、`intellifold/` 和 `protenix/` 下的 `bin/python` 当前返回 `Permission denied`。共享库另有[模型说明](/n1_ssd1/share/models/README.txt)和[文件大小清单](/n1_ssd1/share/models/MANIFEST.tsv)。

## RFD4-Proteina 蛋白质设计模型

代码仓库位于 `/n2_ssd1/users/zilu.zhang/RFD4-Proteina`，权重根目录为 `/n2_ssd1/users/zilu.zhang/rfd4_weights`。两份 checkpoint 均已核实可读。

| 组件 | 相对于权重根目录的文件路径 | 大小 |
| --- | --- | ---: |
| Flow 模型 | `flow_checkpoints/rfd4_proteina_flow-ema.ckpt` | 1.63 GiB |
| 自编码器（AE） | `ae_checkpoints/rfd4_proteina_ae-ema.ckpt` | 981.7 MiB |
