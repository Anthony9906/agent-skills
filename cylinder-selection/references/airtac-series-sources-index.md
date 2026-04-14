# Airtac Series Sources Index

## 用途

这个索引用于在 `references/Airtac-Series-Sources/` 中快速定位亚德客系列图片资料。

它只提供轻量级导航，不替代实际看图：
- 给出每个系列目录的图片数和原 PDF 页范围
- 给出首图 / 中段图 / 尾图三个起读入口
- 给出按任务目标的默认开图顺序

## 已验证的扫描启发

以下模式基于已抽检样本，结论状态为“高概率”，不是硬规则：
- `033-ACQ`、`013-SC+SCL+SCF+BSC` 的首图偏产品概览、理论出力或基础规格
- `033-ACQ` 的中段图包含规格、行程和订购码信息
- `033-ACQ`、`071-HRQ`、`085-HFZ+HFK` 的尾图偏附件、安装、使用注意或尺寸相关内容

因此默认读取策略是：
- 要看概览 / 理论出力 / 基础规格：先开首图，再看相邻后 1~2 张
- 要看订购码 / 变体 / 行程表：先开中段图，再向前后各扩 1~2 张
- 要看安装尺寸 / 附件 / 使用注意：先开尾图，再向前回看 1~2 张

## 系列导航表

| 系列目录 | 图片数 | 原 PDF 页范围 | 首图（概览/规格优先） | 中段图（订购码/变体优先） | 尾图（尺寸/附件优先） |
|----------|--------|---------------|------------------------|----------------------------|------------------------|
| 013-SC+SCL+SCF+BSC | 18 | 0039-0056 | page-0001-src-0039.png | page-0009-src-0047.png | page-0018-src-0056.png |
| 022-PB+PBR | 8 | 0084-0091 | page-0001-src-0084.png | page-0004-src-0087.png | page-0008-src-0091.png |
| 033-ACQ | 14 | 0134-0147 | page-0001-src-0134.png | page-0007-src-0140.png | page-0014-src-0147.png |
| 041-MU | 4 | 0154-0157 | page-0001-src-0154.png | page-0002-src-0155.png | page-0004-src-0157.png |
| 042-MD MK | 6 | 0158-0163 | page-0001-src-0158.png | page-0003-src-0160.png | page-0006-src-0163.png |
| 044-MPE | 4 | 0168-0171 | page-0001-src-0168.png | page-0002-src-0169.png | page-0004-src-0171.png |
| 045-TN TR | 6 | 0172-0177 | page-0001-src-0172.png | page-0003-src-0174.png | page-0006-src-0177.png |
| 046-TC | 6 | 0178-0183 | page-0001-src-0178.png | page-0003-src-0180.png | page-0006-src-0183.png |
| 052-HLF | 6 | 0197-0202 | page-0001-src-0197.png | page-0003-src-0199.png | page-0006-src-0202.png |
| 053-STW | 8 | 0203-0210 | page-0001-src-0203.png | page-0004-src-0206.png | page-0008-src-0210.png |
| 061-RMS | 4 | 0255-0258 | page-0001-src-0255.png | page-0002-src-0256.png | page-0004-src-0258.png |
| 062-RMT | 5 | 0259-0263 | page-0001-src-0259.png | page-0003-src-0261.png | page-0005-src-0263.png |
| 071-HRQ | 8 | 0271-0278 | page-0001-src-0271.png | page-0004-src-0274.png | page-0008-src-0278.png |
| 072-HRS | 3 | 0279-0281 | page-0001-src-0279.png | page-0002-src-0280.png | page-0003-src-0281.png |
| 085-HFZ+HFK | 10 | 0308-0317 | page-0001-src-0308.png | page-0005-src-0312.png | page-0010-src-0317.png |
| 086-HFKP_New | 6 | 0318-0323 | page-0001-src-0318.png | page-0003-src-0320.png | page-0006-src-0323.png |
| 093-QCK | 5 | 0356-0360 | page-0001-src-0356.png | page-0003-src-0358.png | page-0005-src-0360.png |
| 102-TWH TWM | 4 | 0399-0402 | page-0001-src-0399.png | page-0002-src-0400.png | page-0004-src-0402.png |
