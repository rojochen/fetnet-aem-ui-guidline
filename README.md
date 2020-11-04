# Introduction



為了便於行銷與開發人員使用，製作此文件提供設計說明、使用時機與原始碼。在原始碼中會附上每個 component 與 template 需帶入的資料與結果。

## Resources

* **Zeplin** 可從 zeplin 上參考樣式設定與下載圖檔 [https://zpl.io/bLnOR0Q](https://zpl.io/bLnOR0Q)
* **GitLab** 從 GitLab 下載開發環境進行建置 [https://github.com/rojochen/fetnet-ebu-ui.git](//github.com/rojochen/fetnet-ebu-ui.git)

## Installation

本次開發使用 React 作為開發基底，從 Gitlab 下載至本機端後，請在 terminal 執行以下語法。

React 開發規範請參照官方文件：[https://zh-hant.reactjs.org/docs/getting-started.html](https://zh-hant.reactjs.org/docs/getting-started.html)

```text
# 進入專案資料夾
cd fetnet-react

# 安裝套件
npm install

# 進行開發
npm start

# 發布
npm run build
```

## React Third-party plugin

**React Helmet**

[https://github.com/nfl/react-helmet](https://github.com/nfl/react-helmet)

可根據頁面需求改變 `<head>` 資訊，如標題、關鍵字等等。

**React Scroll Parallax**

[https://github.com/jscottsmith/react-scroll-parallax](https://github.com/jscottsmith/react-scroll-parallax)

捲動視差套件，用於背景箭頭的位移。

**React Slick** [https://react-slick.neostack.com/](https://react-slick.neostack.com/)

輪播圖套件，應用性廣，可一次顯示多項 carousel item

**React Spring**

[https://www.react-spring.io/](https://www.react-spring.io/)

若有需要處理局部動態效果，可使用 react-spring 做設定。

**React Visibility Sensor**

[https://www.npmjs.com/package/react-visibility-sensor](https://www.npmjs.com/package/react-visibility-sensor)

偵測區塊是否進入畫面範圍，可進行淡入或其他互動效果。

## Compass

樣式設定使用 Compass 以便未來做 spirit image 的開發，與 retina image 的判讀。Compass 使用說明，請參考官方文件：[http://compass-style.org/](http://compass-style.org/)

**前綴字**

元件為避免樣式名稱與其它套件衝突，編寫元件時皆使用前贅字 `fui-` 。

## 資料結構

主要開發結構如下

* public
* src

## 建置邏輯

1. 從文字、顏色等基礎開始，設定主要樣式
2. 搭配按鈕、選單 等 HTML 屬性建立對應的 元件（element）
3. 根據互動與設計需求，組合不同元件成為組件（component）
4. 根據畫面不同區塊，使用元件與組件，製作可重複使用帶入資料的模板（template）
5. 拼湊不同的模板成為完整的網頁且給予固定網址與名稱（pages）

