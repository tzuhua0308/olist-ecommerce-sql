# Olist 巴西電商 SQL 分析
## Brazilian E-Commerce — SQL Exploratory Analysis

---

### 專案簡介

使用 Olist 巴西電商公開資料集（Kaggle），以 **SQLite + Python** 對 ~100,000 筆訂單進行端對端分析。  
核心目標：展示多表 JOIN、CTE、Window Function 等 SQL 技術，並搭配視覺化呈現商業洞察。

---

### 資料集

| 項目 | 說明 |
|---|---|
| 來源 | [Kaggle — Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) |
| 時間區間 | 2016–2018 |
| 訂單數 | ~100,000 筆 |
| 資料表 | 9 張（訂單、商品、付款、評價、賣家、客戶、物流等） |
| 授權 | CC BY-NC-SA 4.0 |

---

### 分析主題

| Section | 主題 | SQL 技術 |
|---|---|---|
| 1 | 訂單整體概況（GMV、月趨勢） | `GROUP BY` · `strftime` |
| 2 | 客戶分析（地理分布、回購率、LTV） | `CTE` · `NTILE() OVER` · `CASE WHEN` |
| 3 | 賣家績效排名 | `CTE` · `RANK() OVER` |
| 4 | 商品品類分析 | 5 表 `JOIN` · 翻譯表 `COALESCE` |
| 5 | 物流分析（配送天數、準時率） | `JULIANDAY` · `SUM() OVER` |
| 6 | 評分分析（最佳 / 最差品類） | `CTE` · `RANK() OVER` |

---

### 主要結論

- 巴西 SP 州佔總訂單 **42%**，高度集中在東南部
- 回購率僅 **~3%**，電商以一次性購買為主
- Top 25% 客戶（Q4）LTV 遠高於底層，具備高價值分層空間
- 準時配送率 **~92%**，遠距州（AM、RR）平均配送超過 25 天
- 最高評分品類：`fashion_childrens_clothes`；最低：`security_and_services`

---

### 快速開始

```bash
# 1. 下載資料集
pip install kaggle
kaggle datasets download -d olistbr/brazilian-ecommerce
unzip brazilian-ecommerce.zip -d data/

# 2. 安裝套件
pip install -r requirements.txt

# 3. 開啟 notebook
jupyter notebook olist-ecommerce-sql.ipynb
```

> **Kaggle API Token**：至 [kaggle.com/settings](https://www.kaggle.com/settings) → API → Create New Token，將 `kaggle.json` 放至 `~/.kaggle/kaggle.json`。

---

### 專案結構

```
olist-ecommerce-sql/
├── olist-ecommerce-sql.ipynb   # 主要分析 notebook（含輸出）
├── generate_notebook.py        # notebook 產生腳本
├── requirements.txt
├── .gitignore
└── README.md
```

---

### 技術棧

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![SQLite](https://img.shields.io/badge/SQLite-3-lightgrey)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)

`sqlite3` · `pandas` · `matplotlib` · `seaborn`
