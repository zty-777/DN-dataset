# 论文数据集

只含流数据和特征，不含模型、实验结果、划分、代码或日志。各次使用的相同 JSON 已合并去重，未重新抽样。

| 类别 | 正样本 | 负样本 |
|---|---:|---:|
| Obfs4 | 1,500 | 3,500 |
| Snowflake | 772 | 1,804 |
| Meek | 1,542 | 3,164 |
| WebTunnel | 496 | 700 |

- 四个类别目录：`positive/json` 为正样本，`negative/json` 为负样本，`features.csv` 按 `sample_id` 对应同名 JSON；`label=1` 为正，`label=0` 为负。前两列为标识与标签，后续列为模型特征。
- `positive/pcap`：现存且已核对的逐流抓包，共 2 份；名称与对应 JSON 相同。其他 JSON 不代表有完整 PCAP。
- `background/CESNET-TLS22`：按来源日期存放，共 2,000,000 条背景流。每个日期的 `flows.csv.gz` 与两个特征 CSV 逐行对应。
- `background/MAWI`：共 1,012,596 条背景流；JSONL 按文件名排序后依次读取，与 `obfs4_features.csv.gz` 逐行对应。
- 背景目录中的流均为负样本；CESNET 用于 Meek/WebTunnel，MAWI 用于 Obfs4。`.gz` 为 gzip 压缩，可由 Pandas 直接读取。
- JSON 保留原提取内容，可能含来源元数据；建模请使用专门的特征 CSV。
