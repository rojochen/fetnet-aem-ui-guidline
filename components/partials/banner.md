# Banner

## AdaptHeightBanner

```
import AdaptHeightBanner from '../../components/partials/banner/AdaptHeightBanner';
<AdaptHeightBanner
  height={{
    desktop: 360,
    mobile: 180
  }}
  bgImg={{
    md: '/resources/cbu/img/cbu-eservice-service-announcement-1920x360.jpg',
    sm: '/resources/cbu/img/cbu-eservice-service-announcement-750x400.jpg',
  }}
  title='服務公告'
/>
```

#### Properties

| 名稱  | 屬性   | 選項 | 必填 | 說明                                       |
| :---- | :----- | :--- | :--- | :----------------------------------------- |
| bgImg | obj    |      |      | md: PropTypes.string,sm: PropTypes.string, |
| title | string |      |      |                                            |

## ArticleBanner

```
import ArticleBanner from '../../components/partials/banner/ArticleBanner';
<ArticleBanner
  sm='/resources/cbu/life-circle-article/images/cbu-lifecircle-hero-1920x360.jpg'
  md='/resources/cbu/life-circle-article/images/cbu-lifecircle-hero-1920x360.jpg'
  title='開箱智慧生活'
  desc='2020居家必備的一組吸塵器！無線、高續航、配件齊全萬元初'>
</ArticleBanner>
```

#### Properties

| 名稱       | 屬性   | 選項 | 必填 | 說明 |
| :--------- | :----- | :--- | :--- | :--- |
| sm         | string |      |      |      |
| md         | string |      |      |      |
| alt        | string |      |      |      |
| titleColor | string |      |      |      |
| descColor  | string |      |      |      |
| titleColor | string |      |      |      |
| title      | string |      | true |      |
| desc       | string |      | true |      |

## Banner_m

```
import BannerM from '../../components/partials/banner/Banner_m';
<BannerM
  {...{
    patternColor: 'green',
    title: `BannerM`,
    action: [
      {
        text: '了解集客行銷',
        line: '#',
        target: '_blank',
        btnStyle: 'primary'
      },
      {
        text: '聯絡我們',
        line: '#',
        target: '_blank',
      }
    ]
  }
  }
/>
```

#### Properties

| 名稱         | 屬性   | 選項 | 必填 | 說明                                                                     |
| :----------- | :----- | :--- | :--- | :----------------------------------------------------------------------- |
| patternColor | string |      |      |                                                                          |
| title        | string |      |      |                                                                          |
| id           | string |      |      |                                                                          |
| action       | arry   |      |      | text: PropTypes.string,link: PropTypes.string,btnStyle: PropTypes.string |

## BannerPromotionBasic

```
import BannerPromotionBasic from '../../components/partials/banner/BannerPromotionBasic';
<BannerPromotionBasic
  className="is-height-460"
  slides={[
    {
      image: {
        md: '/resources/cbu/img/cbu-promotion-life-1920x460.jpg',
        sm: '/resources/cbu/img/cbu-promotion-life-750x720.jpg'
      },
      tag: null,
      theme: 'dark',
      title: '<div class="mt-7">遠傳心生活，用心嚴選有感回饋</div>',
      description: '<div class="is-text-white">三大特色讓您一手掌握，現在就來體驗「遠傳心生活」!</div>',
      actions: [
        {
          btnStyle: 'primary',
          target: '_self',
          type: 'link',
          text: '立即下載',
          link: '#goodie'
        }
      ]
    }
  ]}
/>
```
#### Properties

| 名稱      | 屬性   | 選項 | 必填 | 說明                                                                                                                                               |
| :-------- | :----- | :--- | :--- | :------------------------------------------------------------------------------------------------------------------------------------------------- |
| slides    | array  |      | true | image: PropTypes.obj, theme: PropTypes.string,tag: PropTypes.string,title: PropTypes.string,description: PropTypes.string,actions: PropTypes.array |
| className | string |      |      |                                                                                                                                                    |
| bgColor   | string |      |      |                                                                                                                                                    |
| openModal | func   |      |      |                                                                                                                                                    |

## BannerWithLink

```
import BannerWithLink from '../../components/partials/banner/BannerWithLink';
<BannerWithLink
  id="hotspot"
  title='熱點查詢'
  image={{
    md: '/resources/cbu/otherService/img-wifi-hotspot-lg.jpg',
    sm: '/resources/cbu/otherService/img-wifihotspot-mobile.jpg',
  }}
  bannerTitle='遍佈全台的 Wi-Fi 熱點'
  bannerDescription='<p>FET Wi-Fi 在全國擁有超過 10,000 個熱點，現在就開始搜尋離你最近的 Wi-Fi 熱點吧！</p>'
  bannerAction={{
    text: '查詢遠傳門市',
    link: '#',
    target: '_self'
  }}
  link={[
    {
      title: '查詢全虹門市',
      link: "#",
      target: '_blank'
    },
    {
      title: '查詢全家便利商店門市',
      link: "#"
    },
    {
      title: '查詢萊爾富便利商店門市',
      link: "#"
    }
  ]}
/>
```

#### Properties

| 名稱              | 屬性   | 選項 | 必填 | 說明                                       |
| :---------------- | :----- | :--- | :--- | :----------------------------------------- |
| id                | string |      |      |                                            |
| title             | string |      |      |                                            |
| image             | array  |      |      | md: PropTypes.string,sm: PropTypes.string, |
| bannerTitle       | string |      |      |                                            |
| bannerDescription | string |      |      |                                            |
| link              | array  |      |      |                                            |

## CbuBanner

```
const bannerTab = {
  tabs: {
    name: 'EbuBannerTab',
    list: [
      {
        // link: '/index/phone',
        name: 'tab-1',
        icon: '/resources/cbu/cbu-index/phone.svg',
        focusIcon: '/resources/cbu/cbu-index/phone-active.svg',
        label: '手機',
      },
      {
        // link: '/index/rate',
        name: 'tab-2',
        icon: '/resources/cbu/cbu-index/pay.svg',
        focusIcon: '/resources/cbu/cbu-index/pay-active.svg',
        label: '資費',
      },
      {
        // link: '/index/lifecircle',
        name: 'tab-3',
        icon: '/resources/cbu/cbu-index/lifestyle.svg',
        focusIcon: '/resources/cbu/cbu-index/lifestyle-active.svg',
        label: '生活圈',
      },
      {
        // link: '/index/discount',
        name: 'tab-4',
        icon: '/resources/cbu/cbu-index/promotion.svg',
        focusIcon: '/resources/cbu/cbu-index/promotion-active.svg',
        label: '優惠',
      },
      {
        // link: '/index/service',
        name: 'tab-5',
        icon: '/resources/cbu/cbu-index/service.svg',
        focusIcon: '/resources/cbu/cbu-index/service-active.svg',
        label: '服務',
      },
    ],
  },
  tabContent: [
    {
      backgroundColor: 'red',
      image: {
        md: '/resources/cbu/cbu-index/kv-red@2x.jpg',
        sm: '/resources/cbu/cbu-index/kv-bg-sm.jpg',
      },
      subOption: [
        {
          md: '/resources/cbu/cbu-index/kv-red@2x.jpg',
          sm: '/resources/cbu/cbu-index/kv-bg-sm@2x.jpg',
        },
        {
          md: '/resources/cbu/cbu-index/kv-red@2x.jpg',
          sm: '/resources/cbu/cbu-index/kv-bg-sm@2x.jpg',
        },
      ],
      content: {
        dropdown: [
          {
            text: '地表最佳拍照手機大比拼1',
            value: '地表最佳拍照手機大比拼1',
            actions: [
              {
                text: '查看',
                link: '/',
              },
              {
                text: '查看',
                link: '/',
              }
            ],
          }
        ],
        tags: [
          {
            text: 'Airpods',
            link: '#'
          },
          {
            text: 'iPhone 11',
            link: '#'
          },
          {
            text: 'Note 10',
            link: '#'
          }
        ]
      },
      promotion: {
        image: {
          default: '/resources/cbu/cbu-index/promo-iphone.png',
          retina: '/resources/cbu/cbu-index/promo-iphone@2x.png'
        },
        title: '遠傳 iPhone 11 享樂1+1',
        description: '帶走最新 AirPods，免費再送 friDay影音',
        action: {
          text: '更多詳情',
          link: '#',
          target: '_blank'
        }
      }
    },
    {
      image: {
        md: '/resources/cbu/cbu-index/kv-bg.jpg',
        sm: '/resources/cbu/cbu-index/kv-bg-sm.jpg',
      },
      subOption: [
        {
          md: '/resources/cbu/cbu-index/kv-bg.jpg',
          sm: '/resources/cbu/cbu-index/kv-bg-sm.jpg',
        },
        {
          md: '/resources/cbu/cbu-index/kv-bg.jpg',
          sm: '/resources/cbu/cbu-index/kv-bg-sm.jpg',
        },
      ],
      content: {
        dropdown: [
          {
            text: '嚴選網路門市限定方案',
            value: '嚴選網路門市限定方案',
            actions: [
              {
                text: '查看',
                link: '/',
              }
            ],
          },
          {
            text: '嚴選網路門市限定方案',
            value: '嚴選網路門市限定方案',
            actions: [
              {
                text: '查看',
                link: '/',
              }
            ],
          },
        ],
        tags: [
          {
            text: '老客戶續約',
            link: '#',
          },
          {
            text: '499吃到飽',
            link: '#',
          },
          {
            text: '出國上網',
            link: '#',
          },
        ]
      },
      promotion: {
        image: {
          default: '/resources/cbu/cbu-index/promo-applew.png',
          retina: '/resources/cbu/cbu-index/promo-applew@2x.png'
        },
        title: 'Apple Watch Series 5 LTE 11/8上市 現正開放預購',
        // description: '帶走最新 AirPods，免費再送 friDay影音',
        action: {
          text: '更多詳情',
          link: '#',
          target: '_blank'
        }
      }
    },
    {
      image: {
        md: '/resources/cbu/cbu-index/kv-bg.jpg',
        sm: '/resources/cbu/cbu-index/kv-bg-sm.jpg',
      },
      subOption: [
        {
          md: '/resources/cbu/cbu-index/kv-bg.jpg',
          sm: '/resources/cbu/cbu-index/kv-bg-sm.jpg',
        },
        {
          md: '/resources/cbu/cbu-index/kv-bg.jpg',
          sm: '/resources/cbu/cbu-index/kv-bg-sm.jpg',
        },
        {
          md: '/resources/cbu/cbu-index/kv-bg.jpg',
          sm: '/resources/cbu/cbu-index/kv-bg-sm.jpg',
        },
        {
          md: '/resources/cbu/cbu-index/kv-bg.jpg',
          sm: '/resources/cbu/cbu-index/kv-bg-sm.jpg',
        },
      ],
      content: {
        dropdown: [
          {
            text: '享受無限追劇的美好人生 1',
            value: '享受無限追劇的美好人生 1',
            actions: [
              {
                text: '查看',
                link: '/',
              },
            ],
          },
          {
            text: '別再追隨別人將資金用在對的科技上',
            value: '別再追隨別人將資金用在對的科技上',
            actions: [
              {
                text: '查看',
                link: '/',
              },
            ],
          },
          {
            text: '創造全新價值',
            value: '創造全新價值',
            actions: [
              {
                text: '查看',
                link: '/',
              },
            ],
          },
          {
            text: '別再追隨別人的腳步將資金用在對的科技上',
            value: '別再追隨別人的腳步將資金用在對的科技上',
            actions: [
              {
                text: '了解更多3-4',
                link: '/',
              },
            ],
          },
        ],
        tags: [
          {
            text: 'friday影音優質好劇',
            link: '#'
          },
          {
            text: '超值折價券',
            link: '#'
          }
        ]
      },
      promotion: {
        image: {
          default: '/resources/cbu/cbu-index/promo-iphone.png',
          retina: '/resources/cbu/cbu-index/promo-iphone@2x.png'
        },
        title: '遠傳 iPhone 11 享樂1+1',
        description: '帶走最新 AirPods，免費再送 friDay影音',
        action: {
          text: '更多詳情',
          link: '#',
          target: '_blank'
        }
      }
    },
    {
      image: {
        md: '/resources/cbu/cbu-index/kv-bg.jpg',
        sm: '/resources/cbu/cbu-index/kv-bg-sm.jpg',
      },
      subOption: [
        {
          md: '/resources/cbu/cbu-index/kv-bg.jpg',
          sm: '/resources/cbu/cbu-index/kv-bg-sm.jpg',
        },
        {
          md: '/resources/cbu/cbu-index/kv-bg.jpg',
          sm: '/resources/cbu/cbu-index/kv-bg-sm.jpg',
        },
      ],
      content: {
        dropdown: [
          {
            text: 'Uber Eats 新客優惠金',
            value: 'Uber Eats 新客優惠金',
            actions: [
              {
                text: '查看',
                link: '/',
              },
            ],
          },
          {
            text: '別再追隨別人將資金用在對的科技上',
            value: '別再追隨別人將資金用在對的科技上',
            actions: [
              {
                text: '查看',
                link: '/',
              },
            ],
          },
        ],
        tags: [
          {
            text: '優惠一次看',
            link: '#',
          },
          {
            text: '白金會員禮',
            link: '#',
          },
          {
            text: '5G免費上網',
            link: '#',
          },
        ],
      },
      promotion: {
        image: {
          default: '/resources/cbu/cbu-index/promo-travel-online.png',
          retina: '/resources/cbu/cbu-index/promo-travel-online@2x.png'
        },
        title: '送日本上網吃到飽 再享冬遊北海道',
        description: '帶走最新 AirPods，免費再送 friDay影音',
        action: {
          text: '更多詳情',
          link: '#',
          target: '_blank'
        }
      }
    },
    {
      image: {
        md: '/resources/cbu/cbu-index/kv-bg.jpg',
        sm: '/resources/cbu/cbu-index/kv-bg-sm.jpg',
      },
      content: {
        links: [
          {
            text: '看帳單',
            link: '#',
          },
          {
            text: '想繳費',
            link: '#',
          },
          {
            text: '查上網用量',
            link: '#',
          },
          {
            text: '查交易記錄',
            link: '#',
          },
          {
            text: '查合約資訊',
            link: '#',
          }
        ],
      },
      promotion: {
        image: {
          default: '/resources/cbu/cbu-index/promo-service-fox.png',
          retina: '/resources/cbu/cbu-index/promo-service-fox@2x.png'
        },
        title: '聰明的愛講智慧音箱',
        description: '帶走最新 AirPods，免費再送 friDay影音',
        action: {
          text: '更多詳情',
          link: '#',
          target: '_blank'
        }
      }
    },
  ],
};
import CbuBanner from '../components/partials/banner/CbuBanner'
<CbuBanner {...Mock.bannerTab} />
```

#### Properties

| 名稱       | 屬性   | 選項 | 必填 | 說明 |
| :--------- | :----- | :--- | :--- | :--- |
| tabs       | obj    |      |      |      |
| tabContent | string |      |      |      |
| onChange   | string |      |      |      |

```
CbuBanner.propTypes = {
  tabs: PropTypes.shape({
    name: PropTypes.string,
    list: PropTypes.arrayOf(
      PropTypes.shape({
        link: PropTypes.string,
        icon: PropTypes.string,
        focusIcon: PropTypes.string,
        label: PropTypes.string.isRequired,
      })
    ),
  }),
  tabContent: PropTypes.arrayOf(
    PropTypes.shape({
      subOption: PropTypes.arrayOf(
        PropTypes.shape({
          md: PropTypes.string,
          retinaMd: PropTypes.string,
          sm: PropTypes.string,
          retinaSm: PropTypes.string,
        })
      ),
      image: PropTypes.shape({
        md: PropTypes.string,
        retinaMd: PropTypes.string,
        sm: PropTypes.string,
        retinaSm: PropTypes.string,
      }),
      backgroundColor: PropTypes.string,   // red || lightgray || black || blue || pink || gold || teal
      content: PropTypes.shape({
        // title: PropTypes.string,
        // actions: PropTypes.arrayOf(PropTypes.objectOf(Button))
      }),
    })
  ),
  onChange: PropTypes.func,
};
```

## EStoreBanner

```
import EStoreBanner from '../../components/partials/banner/EStoreBanner'
<EStoreBanner {...{
  slides: [
    {
      image: {
        md: '/resources/cbu/estore/estore-banner-1440-x-460@2x.jpg',
        sm: '/resources/cbu/estore/estore-banner-m@2x.jpg'
      },
      tag: '網路限定',
      title: '499吃到飽不限速',
      description: 'iPhone11系列送遠傳friDay90天，再送手機保險3個月',
      actions: [{text:'線上申辦', link: '', btnStyle: 'primary'}],
    },
    {
      image: {
        md: '/resources/cbu/estore/estore-banner-1440-x-460@2x.jpg',
        sm: '/resources/cbu/estore/estore-banner-m@2x.jpg'
      },
      tag: '網路限定',
      title: '499吃到飽不限速',
      description: 'iPhone11系列送遠傳friDay90天，再送手機保險3個月',
      actions: [{text:'線上申辦', link: '', btnStyle: 'primary'}],
    }
  ]
}} />
```

#### Properties

| 名稱   | 屬性  | 選項 | 必填 | 說明 |
| :----- | :---- | :--- | :--- | :--- |
| slides | array |      |      |      |

```
EStoreBanner.propTypes = {
  slides: PropTypes.arrayOf(
    PropTypes.shape({
      image: PropTypes.shape({
        md: PropTypes.string,
        sm: PropTypes.string
      }),
      tag: PropTypes.string,
      title: PropTypes.string,
      description: PropTypes.string,
      actions: PropTypes.arrayOf(
        PropTypes.shape({
          text: PropTypes.string,
          link: PropTypes.string,
          target: PropTypes.string,
        })
      )
    })
  )
}
```

## ExclusiveBanner

```
import ExclusiveBanner from '../../components/partials/banner/ExclusiveBanner';
<ExclusiveBanner slides={[{ ...{
  image: { md: '', sm: '' }, title: '', description: '', actions: [{ text: '', link: '' }]
} }]} openModal={this.openModal} />
```

#### Properties

| 名稱   | 屬性  | 選項 | 必填 | 說明 |
| :----- | :---- | :--- | :--- | :--- |
| slides | array |      |      |      |

```
ExclusiveBanner.propTypes = {
  slides: PropTypes.arrayOf(
    PropTypes.shape({
      image: PropTypes.shape({
        md: PropTypes.string,
        sm: PropTypes.string,
      }),
      tag: PropTypes.string,
      title: PropTypes.string,
      description: PropTypes.string,
      actions: PropTypes.arrayOf(
        PropTypes.shape({
          text: PropTypes.string,
          link: PropTypes.string,
          target: PropTypes.string,
        })
      ),
    })
  ),
  openModal: PropTypes.func,
};
```

## FaqBanner
```
import FaqBanner from '../components/partials/banner/FaqBanner';
<FaqBanner
  bgImg={{
    md: '/resources/cbu/e-service/images/cbu-form-banner-1440-x-156.png',
    sm: '/resources/cbu/e-service/images/cbu-form-banner-375-x-147.png'
  }}
  keyword={{
    defaultKeyword: [
      'Gogoro',
      'Gogoro 699',
      'google',
      'GPS',
      'GPS Google',
      'Gogo',
      'GoPro',
      'Geo',
      'SEO',
      'OPPO',
    ],
    path: '/help-center/search',
    placeholder: '請輸入關鍵字'
  }}
  hot={{
    path: '/help-center/search',
    hotword: [
      '遠傳物聯網',
      '雲端運算',
      '主機代管',
      '大寬頻企業',
      'Office 365',
      '007 國際電話',
      '007 國際電話',
      '007 國際電話',
      '大寬頻企業',
    ]
  }}
/>
```

#### Properties

| 名稱    | 屬性 | 選項 | 必填 | 說明 |
| :------ | :--- | :--- | :--- | :--- |
| bgImg   | obj  |      |      |      |
| keyword | obj  |      |      |      |
| hot     | obj  |      |      |      |

```
FaqBanner.propTypes = {
  bgImg: PropTypes.shape({
    md: PropTypes.string,
    sm: PropTypes.string
  }),
  keyword: PropTypes.shape({
    defaultKeyword: PropTypes.arrayOf(
      PropTypes.string
    ),
    path: PropTypes.string,
    placeholder: PropTypes.string
  }),
  hot: PropTypes.shape({
    hotword: PropTypes.arrayOf(
      PropTypes.string
    ),
    path: PropTypes.string
  })
}
```

## FindItemBanner

```

import FindItemBanner from '../../components/partials/banner/FindItemBanner';
<FindItemBanner
  title='商品配送說明'
  image={{
    md: '/resources/cbu/help-center/images/ebu-helpcenter-call-banner.png',
    sm: '/resources/cbu/help-center/images/ebu-helpcenter-call-banner-sm.jpg'
  }}
/>
```

#### Properties

| 名稱  | 屬性   | 選項 | 必填 | 說明 |
| :---- | :----- | :--- | :--- | :--- |
| title | string |      |      |      |
| image | obj    |      |      |      |
```
FindItemBanner.propTypes = {
  title: PropTypes.string,
  image: PropTypes.shape({
    md: PropTypes.string,
    sm: PropTypes.string,
  }),
}
```


## FormBanner
```
import FormBanner from '../components/partials/banner/FormBanner';
<FormBanner
  title="密碼變更"
  image={{
    md: '/resources/cbu/e-service/images/cbu-form-banner-1440-x-156.png',
    sm: '/resources/cbu/e-service/images/cbu-form-banner-375-x-147.png',
  }} 
/>
```

#### Properties

| 名稱      | 屬性   | 選項 | 必填 | 說明 |
| :-------- | :----- | :--- | :--- | :--- |
| image     | obj    |      | true |      |
| title     | string |      | true |      |
| className | string |      |      |      |

```
FormBanner.propTypes = {
    image: PropTypes.shape({
        sm: PropTypes.string.isRequired,
        md: PropTypes.string.isRequired
    }).isRequired,
    title: PropTypes.string.isRequired,
    className: PropTypes.string
}
```

## HelpCenterBanner

```
import HelpCenterBanner from '../../components/partials/banner/HelpCenterBanner';
<HelpCenterBanner
  title={"需要什麼幫助?"}
  bgImg={{
    sm: "/resources/cbu/help-center/images/ebu-helpcenter-home-banner-sm.jpg",
    md: "/resources/cbu/help-center/images/ebu-helpcenter-home-banner.jpg",
  }}
  keyword={{
    defaultKeyword: [
      'Gogoro',
      'Gogoro 699',
      'google',
      'GPS',
      'GPS Google',
      'Gogo',
      'GoPro',
      'Geo',
      'SEO',
      'OPPO',
    ],
    path: '/help-center/search',
    placeholder: '找個人用戶常見問題'
  }}
  hot={{
    path: '/help-center',
    hotword: [
      '遠傳物聯網',
      '雲端運算',
      '主機代管',
      '大寬頻企業光纖',
      'Office 365',
      '007 國際電話',
      '世界電話國碼',
      '世界電話國碼',
      '世界電話國碼',
      '世界電話國碼',
    ]
  }}
/>
```

| 名稱    | 屬性   | 選項 | 必填 | 說明 |
| :------ | :----- | :--- | :--- | :--- |
| title   | string |      |      |      |
| bgImg   | obj    |      |      |      |
| keyword | obj    |      |      |      |
| hot     | obj    |      |      |      |

```
HelpCenterBanner.propTypes = {
  title: PropTypes.string,
  bgImg: PropTypes.shape({
    md: PropTypes.string,
    sm: PropTypes.string,
  }),
  keyword: PropTypes.shape({
    defaultKeyword: PropTypes.arrayOf(PropTypes.string),
    path: PropTypes.string,
    placeholder: PropTypes.string,
  }),
  hot: PropTypes.shape({
    hotword: PropTypes.arrayOf(PropTypes.string),
    path: PropTypes.string,
  }),
};
```

## LifeCircleBanner
```
import LifeCircleBanner from '../../components/partials/banner/LifeCircleBanner';
<LifeCircleBanner {...{
  mainBanner: true,
  slogan: {
    md: '/resources/cbu/life-circle-drama/images/life-story-slogan-01.png',
    sm: '/resources/cbu/life-circle-drama/images/life-story-slogan-01-m.png',
  },
  image: {
    md: '/resources/cbu/life-circle-drama/images/cbu-lifestory-banner-01-1920x470.jpg',
    sm: '/resources/cbu/life-circle-drama/images/cbu-lifestory-banner-01-1920x470.jpg',
  },
  link: '#',
  title: '起床一睜開眼，就等不及要追最新的一集嗎？',
  alt: 'alt text',
  icon: '/resources/cbu/life-circle-drama/images/sunrise.svg',
  subtitle: '8:00AM',
  description: '',
  type: 'img-right'
}} />
```

| 名稱         | 屬性   | 選項 | 必填 | 說明 |
| :----------- | :----- | :--- | :--- | :--- |
| id           | string |      |      |      |
| mainBanner   | bool   |      |      |      |
| slogan       | obj    |      |      |      |
| image        | obj    |      |      |      |
| link         | string |      |      |      |
| title        | string |      |      |      |
| alt          | string |      |      |      |
| sloganAlt    | string |      |      |      |
| icon         | string |      |      |      |
| subtitle     | string |      |      |      |
| description  | string |      |      |      |
| type         | string |      |      |      |
| typeonChange | func   |      |      |      |

```
LifeCircleBanner.propTypes = {
  id: PropTypes.string,
  mainBanner: PropTypes.bool,
  slogan: PropTypes.shape({
    md: PropTypes.string,
    sm: PropTypes.string,
  }),
  image: PropTypes.shape({
    md: PropTypes.string,
    sm: PropTypes.string,
  }),
  link: PropTypes.string,
  title: PropTypes.string,
  alt: PropTypes.string,
  sloganAlt: PropTypes.string,
  icon: PropTypes.string,
  subtitle: PropTypes.string,
  description: PropTypes.string,
  type: PropTypes.string,
  onChange: PropTypes.func,
};
```

## SearchBanner
```
import SearchBanner from '../components/partials/banner/SearchBanner';
<SearchBanner
  bgImg={{
    md: '/resources/common/images/ebu-banner-search.png',
    sm: '/resources/common/images/ebu-banner-search.png',
  }}
  keyword={{
    defaultKeyword: [
      'Gogoro',
      'Gogoro 699',
      'google',
      'GPS',
      'GPS Google',
      'Gogo',
      'GoPro',
      'Geo',
      'SEO',
      'OPPO',
    ],
    path: '/search',
    placeholder: '找企業用戶常見問題',
  }}
  hot={{
    path: '/search',
    label: '熱搜',
    hotword: [
      '遠傳物聯網',
      '雲端運算',
      '主機代管',
      '大寬頻企業光纖',
      'Office 365',
      '007 國際電話',
      '世界電話國碼',
      '世界電話國碼',
      '世界電話國碼',
      '世界電話國碼',
    ],
  }}
/>
```

| 名稱       | 屬性   | 選項 | 必填 | 說明 |
| :--------- | :----- | :--- | :--- | :--- |
| bgImg | obj    |      |      |      |
| keyword | obj    |      |      |      |
| hot | obj    |      |      |      |

```
SearchBanner.propTypes = {
  bgImg: {
    md: PropTypes.string,
    sm: PropTypes.string
  },
  keyword: {
    defaultKeyword: PropTypes.arrayOf(
      PropTypes.string
    ),
    path: PropTypes.string,
    placeholder: PropTypes.string
  },
  hot: {
    hotword: PropTypes.arrayOf(
      PropTypes.string
    ),
    path: PropTypes.string
  }
}
```

## SectionBanner2

```
import SectionBanner2 from './SectionBanner2';
<SectionBanner2
  image={this.props.image}
  title={this.props.bannerTitle}
  description={this.props.bannerDescription}
  action={this.props.bannerAction}
/>
```
| 名稱       | 屬性   | 選項 | 必填 | 說明 |
| :--------- | :----- | :--- | :--- | :--- |
|title |string    |      |      |      |
|className |string    |      |      |      |
|description |string    |      |      |      |
|subTitle |string    |      |      |      |
|position |string    |      |      |      |
|image |obj    |      |      |      |
|action |any    |      |      |      |
|onChange |func    |      |      |      |
|bottomBg |string    |      |      |      |
|bgColor |string    |      |      |      |
|topBg |string    |      |      |      |

```
SectionBanner2.propTypes = {
  title: PropTypes.string,
  className: PropTypes.string,
  description: PropTypes.string,
  subTitle: PropTypes.string,
  position: PropTypes.string,
  image: PropTypes.shape({
    md: PropTypes.string,
    retinaMd: PropTypes.string,
    sm: PropTypes.string,
    retinaSm: PropTypes.string,
  }),
  action: PropTypes.any,
  onChange: PropTypes.func,
  bottomBg: PropTypes.string,
  bgColor: PropTypes.string,
  topBg: PropTypes.string,
};
```

## ZipcodeBanner

```
import ZipcodeBanner from '../../components/partials/banner/ZipcodeBanner';
<ZipcodeBanner
  bgImg={{
    md: '/resources/cbu/otherService/cbu-007-banner-1920x470.jpg',
    sm: '/resources/cbu/otherService/cbu-007-750x720.jpg',
  }}
  title='國際電話'
  height={{ desktop: '460', mb: '360' }}
  description='
    <h6 class="mt-1 is-text-regular">
      市話或手機都能用，直撥 007 / 017 即享有高品質通話及優惠費用！
    </h6>'
  action={null} 
/>
```

| 名稱       | 屬性   | 選項 | 必填 | 說明 |
| :--------- | :----- | :--- | :--- | :--- |
| bgImg |obj    |      |      | md: PropTypes.string,sm: PropTypes.string     |  
| title |string|      |      |      |  
|description |string|      |      |      |  
|height |obj|      |      |      |  

```
ZipcodeBanner.propTypes = {
  bgImg: PropTypes.shape({
    md: PropTypes.string,
    sm: PropTypes.string
  }),
  title: PropTypes.string,
  description: PropTypes.string,
  height: PropTypes.object,
}
```