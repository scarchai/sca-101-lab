# sca-101

`sca-101` 用于整理侧信道分析（Side-Channel Analysis，SCA）的基础实验，帮助读者通过可运行的示例了解常见分析方法。目前包含一个针对 AES 的相关功耗分析（Correlation Power Analysis，CPA）实验。

> 请仅将实验用于学习，以及对自己拥有或已获授权的数据和设备进行分析。

## 实验目录

| 路径 | 内容 |
| --- | --- |
| `cpa_aes/CPA_demo.ipynb` | AES CPA 实验 Notebook |
| `cpa_aes/aes_200_plaintext.npy` | 实验使用的明文数据 |
| `cpa_aes/aes_200_trace.npy` | 实验使用的功耗轨迹数据 |
| `requirements.txt` | Python 依赖及版本 |

实验针对 AES 首轮 SubBytes 中间值建立汉明重量（Hamming Weight）假设，并计算假设与功耗轨迹采样点之间的皮尔逊相关系数。通过比较不同密钥字节猜测的最大绝对相关系数，估计 AES 密钥；Notebook 还会绘制相关性图并展示恢复结果与实验密钥的对比。

## 环境准备

建议使用 Python 3 和虚拟环境。在仓库根目录执行：

```bash
python -m venv .venv
```

激活虚拟环境：

```bash
# Windows PowerShell
.\.venv\Scripts\Activate.ps1

# macOS / Linux
source .venv/bin/activate
```

安装依赖：

```bash
python -m pip install -r requirements.txt
```

## 运行实验

在仓库根目录启动 Notebook：

```bash
jupyter notebook
```

然后打开 `cpa_aes/CPA_demo.ipynb`。也可以直接在终端切换到实验目录后启动：

```bash
cd cpa_aes
jupyter notebook CPA_demo.ipynb
```

在 Notebook 中按顺序运行单元格。程序会提示输入要分析的轨迹数量；输入值应不超过数据文件中的轨迹数。运行完成后，可以查看各密钥字节的相关性图、恢复出的密钥以及与实验密钥的逐字节比较。

## 依赖

依赖及固定版本见 [`requirements.txt`](requirements.txt)，其中包括 NumPy、Matplotlib、Jupyter 和 `estraces`。
