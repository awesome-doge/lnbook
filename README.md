# 精通閃電網路 ⚡

[![CC BY-SA 4.0][cc-by-sa-shield]][cc-by-sa]
[![Deploy](https://github.com/awesome-doge/lnbook/actions/workflows/deploy.yml/badge.svg)](https://github.com/awesome-doge/lnbook/actions/workflows/deploy.yml)

<img src="images/cover_thumb.png" width=200 alt="精通閃電網路封面">

**Mastering the Lightning Network** 繁體中文翻譯

> 原著：Andreas M. Antonopoulos、Olaoluwa Osuntokun、Rene Pickhardt
> 翻譯：Dr. Awesome Doge

## 閱讀

| 格式 | 連結 |
|------|------|
| 線上閱讀 | [lnbook-zh.doge.tg](https://lnbook-zh.doge.tg/) |
| EPUB 電子書 | [下載 EPUB](https://lnbook-zh.doge.tg/mastering-lightning-network-zh-TW.epub) |
| PDF 電子書 | [下載 PDF](https://lnbook-zh.doge.tg/mastering-lightning-network-zh-TW.pdf) |

線上版支援全文搜尋 (Ctrl+K)、Dark Mode、手機響應式、離線閱讀 (PWA)。

## 目錄

### 第一部分：基礎篇

| 章節 | 標題 |
|------|------|
| 1 | [簡介](zh-TW/01_introduction.adoc) |
| 2 | [入門指南](zh-TW/02_getting_started.adoc) |
| 3 | [閃電網路運作原理](zh-TW/03_how_ln_works.adoc) |
| 4 | [閃電網路節點軟體](zh-TW/04_node_client.adoc) |
| 5 | [節點操作](zh-TW/05_node_operations.adoc) |

### 第二部分：技術深入篇

| 章節 | 標題 |
|------|------|
| 6 | [閃電網路架構](zh-TW/06_lightning_architecture.adoc) |
| 7 | [支付通道](zh-TW/07_payment_channels.adoc) |
| 8 | [路由與 HTLC](zh-TW/08_routing_htlcs.adoc) |
| 9 | [通道操作與支付轉發](zh-TW/09_channel_operation.adoc) |
| 10 | [洋蔥路由](zh-TW/10_onion_routing.adoc) |
| 11 | [Gossip 協議與通道圖](zh-TW/11_gossip_channel_graph.adoc) |
| 12 | [路徑搜尋與支付傳遞](zh-TW/12_path_finding.adoc) |
| 13 | [Wire 協議](zh-TW/13_wire_protocol.adoc) |
| 14 | [加密訊息傳輸](zh-TW/14_encrypted_transport.adoc) |
| 15 | [閃電網路支付請求](zh-TW/15_payment_requests.adoc) |
| 16 | [安全性與隱私](zh-TW/16_security_privacy_ln.adoc) |
| 17 | [結論](zh-TW/17_conclusion.adoc) |

### 附錄

| 附錄 | 標題 |
|------|------|
| A | [術語表](zh-TW/glossary.adoc) |
| B | [比特幣基礎回顧](zh-TW/appendix_bitcoin_fundamentals_review.adoc) |
| C | [Docker 基礎](zh-TW/appendix_docker_basics.adoc) |
| D | [協議訊息](zh-TW/appendix_protocol_messages.adoc) |

## 本地建置

```bash
# 安裝依賴
gem install asciidoctor asciidoctor-diagram rouge

# 建置 HTML
asciidoctor \
  -D docs \
  -a toc=left -a toclevels=2 -a sectnums \
  -a icons=font -a source-highlighter=rouge \
  -a imagesdir=images -a stem=latexmath \
  -a docinfo=shared \
  -o index.html zh-TW/book.adoc
```

## 專案結構

```
zh-TW/              繁體中文翻譯 (AsciiDoc)
  book.adoc          主入口，引用所有章節
  style.css          自訂樣式（中文排版、Dark Mode、響應式）
  docinfo.html       <head> 注入（字體、CSS、PWA）
  docinfo-footer.html  互動功能 JS（搜尋、TOC、進度條）
  pdf-theme.yml      PDF 電子書排版主題
images/              書籍圖片與示意圖
code/docker/         閃電網路 Docker 實驗環境
docs/                建置輸出（GitHub Pages）
sw.js                Service Worker（離線閱讀）
manifest.json        PWA Manifest
```

## CI/CD

推送到 `develop` 分支自動觸發 [GitHub Actions](.github/workflows/deploy.yml)：

1. Asciidoctor 建置 HTML
2. 圖片無損壓縮 (optipng/jpegoptim)
3. Pagefind 全文搜尋索引
4. EPUB / PDF 電子書生成
5. 部署至 GitHub Pages

## 貢獻

歡迎對翻譯內容提出修正或建議，請透過 [Issue](https://github.com/awesome-doge/lnbook/issues) 或 Pull Request 參與。

### AsciiDoc 格式規範

- 每句一行（方便 diff）
- Unix 換行符 (LF)
- 無尾隨空白或 Tab
- 標題使用 `==`（章）、`===`（節）
- 首次使用縮寫時拼出全名：「雜湊時間鎖定合約 (HTLC)」

## 授權

[![CC BY-SA 4.0][cc-by-sa-image]][cc-by-sa]

本書以 [CC BY-SA 4.0][cc-by-sa] 授權釋出。

原作者：Andreas M. Antonopoulos、Olaoluwa Osuntokun、Rene Pickhardt
原始專案：[lnbook/lnbook](https://github.com/lnbook/lnbook)

[cc-by-sa]: http://creativecommons.org/licenses/by-sa/4.0/
[cc-by-sa-image]: https://licensebuttons.net/l/by-sa/4.0/88x31.png
[cc-by-sa-shield]: https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg
