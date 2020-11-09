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

| 名稱   | 屬性   | 選項 | 必填 | 說明                  |
| :----- | :----- | :--- | :--- | :-------------------- |
| image  | obj    |      |      | default, retina, alt |
| title  | string |      |      |                       |
| description | string |      |      |                       |
| description | action |      |      |text, link, target|
