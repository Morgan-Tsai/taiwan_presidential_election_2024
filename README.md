# 練習專案四 : 找出章魚里

## 簡介

這個專案「找出章魚里」透過中選會選舉及公投資料庫的 [2024 ー 第16任總統副總統選舉](https://db.cec.gov.tw/ElecTable/Election/ElecTickets?dataType=tickets&typeId=ELC&subjectId=P0&legisId=00&themeId=4d83db17c1707e3defae5dc4d4e9c800&dataLevel=N&prvCode=00&cityCode=000&areaCode=00&deptCode=000&liCode=0000) 的資料計算全台灣 7700 餘個村鄰里的得票率，並將其與全國得票率相比較，針對兩個報章媒體的不合理論點提出反思。

1. 人口結構會變動、選舉有不同類型，將一個特定村鄰里訂為長年不變的章魚里是明顯不合理的。
2. 「得票率跟最終結果非常相近」的定義非常模糊。

我們使用了 `pandas` 與 `sqlite3` 建立了資料庫，利用 `numpy` 進行概念驗證並以 `gradio` 做出成品。
可以點選 Hugging Face 的連結<https://huggingface.co/spaces/Morgan2800/taiwan_presidential_election_2024>參考成品

## 專案亮點

- 原始資料是具備合併儲存格與未定義值的多張試算表，透過程式我們可以轉換為理想的資料格式與型態。
- 我們引用了資料科學中用來探勘文字的餘弦相似度，提出更合理的章魚里評估指標。
- 以 `numpy` 與 `pandas` 進行概念驗證。
- 以 `gradio` 做出成品。
- 成品能夠以 Hugging Face Spaces 網址直接訪問。
- 可以重現（Reproducible）。

## 如何重現

- 安裝 [Miniconda](https://docs.anaconda.com/miniconda)
- 依據 `environment.yml` 建立環境：

```bash
conda env create -f environment.yml
```

- 將 `data/` 資料夾中的「總統-A05-4-候選人得票數一覽表-各投開票所」22 個試算表檔案放到專案資料夾的 `data/` 資料夾中
- 啟動環境並執行 `python create_election_2024_db.py` 就能在 `data/` 資料夾中建立 `taiwan_election_2024.db`
- 啟動環境並執行 `python app.py` 並前往 `http://127.0.0.1:7860` 瀏覽成品。

