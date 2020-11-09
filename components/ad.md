# Ad

## FooterAd

An ad block always places in footer

```text
import FooterAd from '../ad/FooterAd';

<FooterAd {...{
  image: {
    md: '/resources/ebu/images/ebu-medium-ad-01.jpg',
    sm: '/resources/ebu/images/ebu-medium-ad-01-sm.jpg',
  },
  title: '您隨身的雲端辦公室，無論在哪都能使用一流的高生產力工具！',
  action: {
    text: '了解Office 365輕享',
    link: '#',
  }
}} />
```



#### Properties

| 名稱            | 屬性   | 選項 | 必填 | 說明                         |
| :-------------- | :----- | :--- | :--- | :--------------------------- |
| image           | Obj    |      |      |                              |
| image.md        | string |      |      | 大網圖                       |
| image.sm        | string |      |      | 小網圖                       |
| title           | string |      |      |                              |
| action          | obj    |      |      |                              |
| action.text     | string |      |      |                              |
| action.link     | string |      |      |                              |
| action.btnStyle | string |      |      | only 'primary' or 'seconday' |

[DEMO](http://fetnet-storybook.aja.com.tw/iframe.html?id=ad--global-banner-ad-01)

## GlobalBannerAd

An global ad block in main body

```text
import GlobalBannerAd from '../components/ad/GlobalBannerAd';

<GlobalBannerAd
  image={{
    md: '/resources/ebu/images/ebu-medium-ad-01.jpg',
    sm: '/resources/ebu/images/ebu-medium-ad-01-sm.jpg',
  }}
  title='開業技法新知盡在【創業開店好幫手】粉絲團開業技法新知盡在【創業開店好幫手】粉絲團開業技法新知盡在【創業開店好幫手】粉絲團開業技法新知盡在【創業開店好幫手】粉絲團'
  action={{
    text: '追蹤 FB',
    link: '#',
  }}
/>
```

#### Properties

| 名稱         | 屬性   | 選項       | 必填 | 說明                  |
| :----------- | :----- | :--------- | :--- | :-------------------- |
| patternColor | string | blue, gray |      | only 'blue' or 'gray' |
| title        | string |            |      |                       |
| action       | object |            |      |                       |

[DEMO](http://fetnet-storybook.aja.com.tw/iframe.html?id=ad--global-banner-ad-01)

## CbuPromotion

```text
import CbuPromotion from '../../ad/CbuPromotion';

<CbuPromotion
  id={tabContent.length - 1 === idx ? `mainView-"${idx + 1}-2` : `mainView-${idx + 1}-3`}
  key={`banner-promotion-${idx}`}
  {...tab.promotion}
/>
```

#### Properties

| 名稱        | 屬性   | 選項 | 必填 | 說明                 |
| :---------- | :----- | :--- | :--- | :------------------- |
| image       | obj    |      |      | default, retina, alt |
| title       | string |      |      |                      |
| description | string |      |      |                      |
| description | action |      |      | text, link, target   |

## SectionAd5

```text
import SectionAd5 from '../../components/ad/SectionAd5';
<SectionAd5 {...{
  image: {
    md: '/resources/cbu/life-circle-curation/images/sidebar-ad.jpg',
    sm: '/resources/cbu/life-circle-curation/images/cbu-promotion-sidebar-750x540.jpg'
  },
  title: '遠傳遠遊卡 friDay聯名卡 卡友專區',
  content: '於friDay購物結帳頁購買遠遊卡並輸入優惠券折抵序號(ftcard)享九折優...',
  action: {
    link: '#',
    text: '了解更多',
  },
}} />
```

#### Properties

| 名稱    | 屬性   | 選項 | 必填 | 說明                                            |
| :------ | :----- | :--- | :--- | :---------------------------------------------- |
| image   | obj    |      |      | md: PropTypes.string, sm: PropTypes.string,     |
| title   | string |      |      |                                                 |
| content | string |      |      |                                                 |
| action  | obj    |      |      | text: PropTypes.string, link: PropTypes.string, |


## SplashPromotion

```text
import SplashPromotion from '../components/ad/SplashPromotion'
<SplashPromotion
  video={{
    cover: {
      md: '/resources/cbu/cbu-index/img-splash-promo@2x.jpg',
      sm: '/resources/cbu/cbu-index/mobile-spash-promotion.jpg',
    },
    alterVideo: 'https://youtu.be/_-P84QjN_G8'
  }}
  title='Google Pixel 4 打造完美手機體驗'
  description='遠傳獨家銷售，現在馬上來體驗'
  action={{
    link: '/',
    text: '立即購買'
  }}
/>
```
#### Properties

| 名稱   | 屬性   | 選項 | 必填 | 說明                                                                                                                               |
| :----- | :----- | :--- | :--- | :--------------------------------------------------------------------------------------------------------------------------------- |
| image  | obj    |      |      | md: PropTypes.string, sm: PropTypes.string,                                                                                        |
| title  | string |      |      |                                                                                                                                    |
| video  | obj    |      |      | alterVideo: PropTypes.string, videoUrl: PropTypes string, cover: PropTypes.shape({ md: PropTypes.string, sm: PropTypes.string, }), |
| action | obj    |      |      | text: PropTypes.string, link: PropTypes string,                                                                                    |
