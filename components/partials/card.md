# card

## ArrowMoreTopRightCarousel

```
import ArrowMoreTopRightCarousel from '../../components/partials/card/ArrowMoreTopRightCarousel';
<ArrowMoreTopRightCarousel {...{
  title: '漫遊優惠',
  more: {
    link: '#',
    text: '看更多',
  },
  cards: [
    {
      image: '/resources/cbu/roaming/roaming-card-img-4@2x.jpg',
      subtitle: '',
      title: '遠傳用戶獨享接機優惠價 $799',
      description: '疫情結束全面啟動旅遊模式，機場接送優惠價，陪你輕鬆出遊安心回家。',
      link: '#',
    },
    {
      image: '/resources/cbu/roaming/roaming-card-img-5@2x.jpg',
      subtitle: '',
      title: '亞洲輕量包 漫遊一天只要 $20',
      description: '自助最佳旅伴全新登場！一天 1G 只要 $20 超划算！',
      link: '#',
    },
    {
      image: '/resources/cbu/roaming/roaming-card-img-4@2x.jpg',
      subtitle: '',
      title: '訂房送帳單折抵金 $1,050',
      description: '於 Booking.com 訂房享有遠傳電信帳單折抵，要搶要快！ ',
      link: '#',
    },
  ],
}} />
```

| 名稱    | 屬性   | 選項 | 必填 | 說明                                                                    |
| :------ | :----- | :--- | :--- | :---------------------------------------------------------------------- |
| title   | string |      |      |                                                                         |
| cards   | array  |      |      |                                                                         |
| bgStyle | string |      |      |                                                                         |
| more    | obj    |      |      | text: PropTypes.string,link: PropTypes.string,target: PropTypes.string, |

## CardFeature

```
import CardFeature from '../../components/partials/card/CardFeature';
<CardFeature
titleColor="white"
topBg="/resources/cbu/img/cbu-goshare-bg-blue-1@2x.jpg"
bottomBg={null}
{...{
  "title": "5月31前，遠傳獨家搶辦",
  "cards": [
    {
      "type": "card01",
      "image": "/resources/cbu/img/promotion-easy@2x.jpg",
      "title": "上網＋網內雙飽，輕鬆配",
      "list": [
        {
          "text": "月付＄699，上網＋網內雙飽"
        },
        {
          "text": "限時加碼，網外最高享1300分鐘"
        }
      ]
    },
    {
      "type": "card01",
      "image": "/resources/cbu/img/promotion-coupon@2x.jpg",
      "title": "每月高額騎乘金，自由騎行",
      "list": [
        {
          "text": "搭配方案享$4,800騎乘金輕鬆GO"
        },
        {
          "text": "小額資費也能享騎乘金"
        }
      ]
    },
    {
      "type": "card01",
      "image": "/resources/cbu/img/promotion-airpods@2x.jpg",
      "title": "最新3C配件免費送，讓你成為穿梭街道的最美風景",
      "list": [
        {
          "text": "最瞎趴AirPods Pro只要$0"
        },
        {
          "text": "Giant都會通勤小折，免費騎"
        }
      ]
    },
    {
      "type": "card01",
      "image": "/resources/cbu/img/promotion-airpods@2x.jpg",
      "title": "最新3C配件免費送，讓你成為穿梭街道的最美風景",
      "list": [
        {
          "text": "最瞎趴AirPods Pro只要$0"
        },
        {
          "text": "Giant都會通勤小折，免費騎"
        }
      ]
    }
  ]
}} />
```

#### Properties

| 名稱       | 屬性   | 選項 | 必填 | 說明 |
| :--------- | :----- | :--- | :--- | :--- |
| title      | string |      |      |      |
| cards      | array  |      |      |      |
| titleColor | array  |      |      |      |
| topBg      | string |      |      |      |
| bottomBg   | string |      |      |      |

```
CardFeature.propTypes = {
  title: PropTypes.string,
  titleColor: PropTypes.string,
  topBg: PropTypes.string,
  bottomBg: PropTypes.string,
  cards: PropTypes.arrayOf(
    PropTypes.shape({
      ribbon: PropTypes.string,
      image: PropTypes.string,
      title: PropTypes.string,
      list: PropTypes.arrayOf(
        PropTypes.shape({
          text: PropTypes.string,
          tooltip: PropTypes.string,
        })
      ),
      action: PropTypes.shape({
        text: PropTypes.string,
        link: PropTypes.string,
        target: PropTypes.string,
      }),
    })
  )
}
```

## CarouselCards

```
import CarouselCards from '../components/partials/card/CarouselCards';
<CarouselCards
  title='網路門市'
  type='product'
  more={{
    text: '前往網路門市',
    link: '#',
  }}
  cards={Mock.productCarousel}
/>
```
#### Properties

| 名稱    | 屬性   | 選項 | 必填 | 說明 |
| :------ | :----- | :--- | :--- | :--- |
| title   | string |      |      |      |
| type    | string |      |      |      |
| cards   | array  |      |      |      |
| bgStyle | string |      |      |      |
| more    | obj    |      |      |      |

## CbuNews

```
import CbuNews from '../components/partials/card/CbuNews'
<CbuNews {...{
  title: '消息與公告',
  tab: {
    name: 'cbu-news-tab',
    list: [
      {
        label: '最新消息'
      },
      {
        label: '服務公告'
      }
    ]
  },
  tabContent: [
    {
      cards: [
        {
          link: '#',
          public_at: '2020/04/21',
          meta: '業務',
          title: '開啟自學模式沒「疫」外！遠傳攜手線上教育領導品牌...'
        },
        {
          link: '#',
          public_at: '2020/04/20',
          meta: '最新消息',
          title: '遠傳推出最強母親節「寵i獻禮」全新iPhone SE 0元起'
        },
        {
          link: '#',
          public_at: '2020/04/19',
          meta: 'CSR',
          title: '響應世界地球日50週年 遠傳呼朋引伴擴大影響力'
        }
      ],
      more: {
        text: '看更多',
        link: '#'
      }
    },
    {
      cards: [
        {
          link: '#',
          public_at: '2020/04/21',
          meta: '業務',
          title: '開啟自學模式沒「疫」外！遠傳攜手線上教育領導品牌...'
        },
        {
          link: '#',
          public_at: '2020/04/20',
          meta: '最新消息',
          title: '遠傳推出最強母親節「寵i獻禮」全新iPhone SE 0元起'
        },
        {
          link: '#',
          public_at: '2020/04/19',
          meta: 'CSR',
          title: '響應世界地球日50週年 遠傳呼朋引伴擴大影響力'
        }
      ],
      more: {
        text: '看更多',
        link: '#'
      }
    }
  ]
}} />
```

#### Properties

| 名稱       | 屬性   | 選項 | 必填 | 說明 |
| :--------- | :----- | :--- | :--- | :--- |
| title      | string |      |      |      |
| tab        | obj    |      |      |      |
| tabContent | array  |      |      |      |

```
CbuNews.propTypes = {
  title: PropTypes.string,
  tab: PropTypes.shape({
    name: PropTypes.string,
    list: PropTypes.arrayOf(
      PropTypes.shape({
        label: PropTypes.string,
      })
    ),
  }),
  tabContent: PropTypes.arrayOf(
    PropTypes.shape({
      more: PropTypes.shape({
        text: PropTypes.string,
        link: PropTypes.string,
      }),
      cards: PropTypes.arrayOf(
        PropTypes.shape({
          link: PropTypes.string,
          public_at: PropTypes.string,
          meta: PropTypes.string,
          title: PropTypes.string,
        })
      ),
    })
  ),
};
```

## ExtraPromotion
```
import ExtraPromotion from '../components/partials/card/ExtraPromotion';
<ExtraPromotion cards={...[
  {
    link: '#',
    title: '聖誕跨年嗨翻天八九十一二三四五六七八九十一二三四',
    description: '每月$203起送吃喝玩樂大禮包 一元 AirPods 買起來!',
  },
  {
    link: '#',
    title: '青春無價，就要給你學生價',
    description: '每月$203起送吃喝玩樂大禮包 一元 AirPods 買起來!',
  },
  {
    link: '#',
    title: '青春無價，就要給你學生價',
    description: '每月$203起送吃喝玩樂大禮包 一元 AirPods 買起來!',
  },
]}
```

#### Properties

| 名稱  | 屬性  | 選項 | 必填 | 說明 |
| :---- | :---- | :--- | :--- | :--- |
| cards | array |      |      |      |

## GroupExtraLinkCard

```
let curationArticle = [
  {
    title: '開箱智慧生活',
    loadMore: true,
    list: [
      {
        id: 'topic-01-1',
        period: '大師戀愛論',
        date: '2019.12.12',
        title: '開箱智慧生活',
        img: '/resources/cbu/life-circle-curation/images/ebu-medium-article-banner-crop.jpg',
        brief: '靈活運用大(大數據)、人(人工智慧)、物(物聯網)技術者，將是個人、企業與國家永續成長的決勝關鍵。',
        link: '#',
        fbLink: '#',
        lineLink: '#',
      },
      {
        id: 'topic-01-2',
        period: '開箱智慧生活',
        date: '2019.12.12',
        title: '智慧城市 Level Up 電信商營運大進化',
        img: '/resources/cbu/life-circle-curation/images/ebu-medium-article-banner-crop.jpg',
        brief: '靈活運用大(大數據)、人(人工智慧)、物(物聯網)技術者，將是個人、企業與國家永續成長的決勝關鍵。',
        link: '#',
        fbLink: '#',
        lineLink: '#',
      },
    ],
  },
  {
    title: '影劇話題',
    loadMore: false,
    list: [
      {
        id: 'topic-02-1',
        period: '影劇話題',
        date: '2019.12.12',
        title: '醫療商機',
        img: '/resources/cbu/life-circle-curation/images/ebu-medium-article-banner-crop.jpg',
        brief: '靈活運用大(大數據)、人(人工智慧)、物(物聯網)技術者，將是個人、企業與國家永續成長的決勝關鍵。',
        link: '#',
        fbLink: '#',
        lineLink: '#',
      },
      {
        id: 'topic-02-2',
        period: '影劇話題',
        date: '2019.12.12',
        title: '智慧城市 Level Up 電信商營運大進化',
        img: '/resources/cbu/life-circle-curation/images/ebu-medium-article-banner-crop.jpg',
        brief: '靈活運用大(大數據)、人(人工智慧)、物(物聯網)技術者，將是個人、企業與國家永續成長的決勝關鍵。',
        link: '#',
        fbLink: '#',
        lineLink: '#',
      },
    ],
  },
  {
    title: '大師戀愛論',
    loadMore: false,
    list: [
      {
        id: 'topic-03-1',
        period: '大師戀愛論',
        date: '2019.12.12',
        title: 'AIOT',
        img: '/resources/cbu/life-circle-curation/images/ebu-medium-article-banner-crop.jpg',
        brief: '靈活運用大(大數據)、人(人工智慧)、物(物聯網)技術者，將是個人、企業與國家永續成長的決勝關鍵。',
        link: '#',
        fbLink: '#',
        lineLink: '#',
      },
    ],
  },
  {
    title: '防疫小確幸',
    loadMore: false,
    list: [
      {
        id: 'topic-04-1',
        period: '防疫小確幸',
        date: '2019.12.12',
        title: '全部期刊',
        img: '/resources/cbu/life-circle-curation/images/ebu-medium-article-banner-crop.jpg',
        brief: '靈活運用大(大數據)、人(人工智慧)、物(物聯網)技術者，將是個人、企業與國家永續成長的決勝關鍵。',
        link: '#',
        fbLink: '#',
        lineLink: '#',
      },
    ],
  },
  {
    title: '健康食代',
    loadMore: false,
    list: [
      {
        id: 'topic-05-1',
        period: '健康食代',
        date: '2019.12.12',
        title: '5G',
        img: '/resources/cbu/life-circle-curation/images/ebu-medium-article-banner-crop.jpg',
        brief: '靈活運用大(大數據)、人(人工智慧)、物(物聯網)技術者，將是個人、企業與國家永續成長的決勝關鍵。',
        link: '#',
        fbLink: '#',
        lineLink: '#',
      },
    ],
  },
  {
    title: '車聯網',
    loadMore: false,
    list: [
      {
        id: 'topic-06-1',
        period: '車聯網',
        date: '2019.12.12',
        title: '車聯網 電信商營運大進化',
        img: '/resources/cbu/life-circle-curation/images/ebu-medium-article-banner-crop.jpg',
        brief: '靈活運用大(大數據)、人(人工智慧)、物(物聯網)技術者，將是個人、企業與國家永續成長的決勝關鍵。',
        link: '#',
        fbLink: '#',
        lineLink: '#',
      },
    ],
  },
  {
    title: '智慧城市',
    loadMore: false,
    list: [
      {
        id: 'topic-07-1',
        period: '智慧城市',
        date: '2019.12.12',
        title: '智慧城市 Level Up 電信商營運大進化',
        img: '/resources/cbu/life-circle-curation/images/ebu-medium-article-banner-crop.jpg',
        brief: '靈活運用大(大數據)、人(人工智慧)、物(物聯網)技術者，將是個人、企業與國家永續成長的決勝關鍵。',
        link: '#',
        fbLink: '#',
        lineLink: '#',
      },
    ],
  },
]
import GroupExtraLinkCard from '../components/partials/card/GroupExtraLinkCard';
<GroupExtraLinkCard article={curationArticle} />
```

#### Properties

| 名稱    | 屬性  | 選項 | 必填 | 說明 |
| :------ | :---- | :--- | :--- | :--- |
| article | array |      |      |      |

```
GroupExtraLinkCard.propTypes = {
  article: PropTypes.arrayOf(
    PropTypes.shape({
      img: PropTypes.string,
      retinaImg: PropTypes.string,
      period: PropTypes.string,
      date: PropTypes.string,
      title: PropTypes.string,
      brief: PropTypes.string,
      link: PropTypes.string,
    })
  ),
};
```

## HappyGoCard
```
import HappyGoCard from '../../components/partials/card/HappyGoCard';
<HappyGoCard {...{
  title: 'HAPPYGO點數折抵',
  more: {
    link: '#',
    text: '看更多',
  },
  className: 'happy-go',
  cards: [
    {
      title: '折抵帳單金額50元',
      description: '<img src="/resources/cbu/img/ic-24-px-fcoin.svg" alt="fcoin" /> 200',
      link: '#',
    },
    {
      title: '折抵帳單金額100元',
      description: '<img src="/resources/cbu/img/ic-24-px-fcoin.svg" alt="fcoin" /> 200',
      link: '#',
    },
    {
      title: '折抵帳單金額300元',
      description: '<img src="/resources/cbu/img/ic-24-px-fcoin.svg" alt="fcoin" /> 200',
      link: '#',
    },
    {
      title: '折抵帳單金額500元',
      description: '<img src="/resources/cbu/img/ic-24-px-fcoin.svg" alt="fcoin" />200',
      link: '#',
    },
  ]
}} />
```

#### Properties

| 名稱      | 屬性   | 選項 | 必填 | 說明 |
| :-------- | :----- | :--- | :--- | :--- |
| title     | string |      |      |      |
| className | string |      |      |      |
| cards     | array  |      |      |      |
| more      | obj    |      |      |      |

```
HappyGoCard.propTypes = {
    title: PropTypes.string,
    className: PropTypes.string,
    cards: PropTypes.arrayOf(
        PropTypes.shape({
            title: PropTypes.string,
            public_at: PropTypes.string,
            meta: PropTypes.string,
            link: PropTypes.string
        })
    ),
    more: PropTypes.shape({
        link: PropTypes.string,
        text: PropTypes.string
    })
}
```

## LifeCircleCarousel

```
import LifeCircleCarousel from '../../components/partials/card/LifeCircleCarousel';
<LifeCircleCarousel {...{
  title: '探索更多生活圈',
  cards: [
    {
      image: '/resources/cbu/life-circle-slashie/images/life-story-thumbnail-05.png',
      title: '追劇人生',
      description: '',
      link: '#',
    },
    {
      image: '/resources/cbu/life-circle-slashie/images/life-story-thumbnail-01.png',
      title: '玩家聯盟時刻',
      description: '',
      link: '#',
    },
    {
      image: '/resources/cbu/life-circle-slashie/images/life-story-thumbnail-02.png',
      title: '週末自煮烘焙日',
      description: '',
      link: '#',
    },
    {
      image: '/resources/cbu/life-circle-slashie/images/life-story-thumbnail-03.png',
      title: '跑山環島騎到飽',
      description: '',
      link: '#',
    },
  ]
}} />
```


#### Properties

| 名稱     | 屬性   | 選項 | 必填 | 說明 |
| :------- | :----- | :--- | :--- | :--- |
| id       | string |      |      |      |
| subtitle | string |      |      |      |
| title    | string |      |      |      |
| cards    | array  |      |      |      |
| bgStyle  | array  |      |      |      |
| more     | obj    |      |      |      |

```
LifeCircleCarousel.propTypes = {
  id: PropTypes.string,
  subtitle: PropTypes.string,
  title: PropTypes.string,
  cards: PropTypes.arrayOf(PropTypes.objectOf(Card)),
  bgStyle: PropTypes.string,
  more: PropTypes.shape({
    text: PropTypes.string,
    link: PropTypes.string,
  }),
};
```

## LifeCircleNewsCarousel

```
import LifeCircleNewsCarousel from '../../components/partials/card/LifeCircleIndexNewsCarousel';
<LifeCircleNewsCarousel {...{
  title: '圈出新聞焦點',
  // more: {
  //   link: '#',
  //   text: '更多話題',
  // },
  cards: [
    {
      subtitle: '',
      image: '/resources/cbu/life-circle-index/images/img-news-1-x-1-1.jpg',
      title: '無疫情沒人戴口罩，而有口罩之亂的瑞士',
      description: '根據新蘇黎世報2月9日最新的全球疫情分析(德)，從疫情爆發至今，瑞士目前尚無確診病例。參與法國撤僑回到歐洲的瑞士人，現...',
      link: '#',
    },
    {
      subtitle: '',
      image: '/resources/cbu/life-circle-index/images/img-news-1-x-1-1.jpg',
      title: '口罩戴久悶熱，不小心就變成敏弱肌',
      description: '身邊開始有朋友說，本來沒有過敏體質，但不知什麼原因，原本換季也都還好，怎麼這次為了防新冠病毒(武漢病毒)，在辦公室或...',
      link: '#',
    },
    {
      subtitle: '',
      image: '/resources/cbu/life-circle-index/images/img-news-1-x-1-1.jpg',
      title: '遊戲人生 | 動物森友會與日常生活的對比',
      description: '這款遊戲近期非常的火紅，除了強打與現實時間同步之外，也可能可以在COVID-19（武漢肺炎）的防疫狀態，給玩家重溫日常生...',
      link: '#',
    },
    {
      subtitle: '',
      image: '/resources/cbu/life-circle-index/images/img-news-1-x-1-1.jpg',
      title: '《無人知曉》瞬間最高收視衝破11%大關',
      description: '《SYK 天空之城》紅遍大街小巷的「金珠英老師」金瑞亨回歸小螢幕新戲《無人知曉》首播瞬間最高收視率衝破11%大關開紅盤。...',
      link: '#',
    },
    {
      subtitle: '',
      image: '/resources/cbu/life-circle-index/images/img-news-1-x-1-1.jpg',
      title: '《無人知曉》瞬間最高收視衝破11%大關',
      description: '《SYK 天空之城》紅遍大街小巷的「金珠英老師」金瑞亨回歸小螢幕新戲《無人知曉》首播瞬間最高收視率衝破11%大關開紅盤。...',
      link: '#',
    },
    {
      subtitle: '',
      image: '/resources/cbu/life-circle-index/images/img-news-1-x-1-1.jpg',
      title: '《無人知曉》瞬間最高收視衝破11%大關',
      description: '《SYK 天空之城》紅遍大街小巷的「金珠英老師」金瑞亨回歸小螢幕新戲《無人知曉》首播瞬間最高收視率衝破11%大關開紅盤。...',
      link: '#',
    },
  ]
}} />
```

#### Properties

| 名稱     | 屬性   | 選項 | 必填 | 說明 |
| :------- | :----- | :--- | :--- | :--- |
| id       | string |      |      |      |
| subtitle | string |      |      |      |
| title    | string |      |      |      |
| cards    | array  |      |      |      |
| bgStyle  | array  |      |      |      |
| more     | obj    |      |      |      |
```
LifeCircleNewsCarousel.propTypes = {
  id: PropTypes.string,
  subtitle: PropTypes.string,
  title: PropTypes.string,
  cards: PropTypes.arrayOf(
    PropTypes.objectOf(Card)
  ),
  bgStyle: PropTypes.string,
  more: PropTypes.shape({
    text: PropTypes.string,
    link: PropTypes.string
  })
}
```

## LifeCircleNewsCarousel
```
import LifeCircleNewsCarousel from '../../components/partials/card/LifeCircleIndexNewsCarousel';
<LifeCircleNewsCarousel {...{
  title: '再忙也要娛樂',
  // more: {
  //   link: '#',
  //   text: '更多話題',
  // },
  cards: [
    {
      subtitle: '',
      image: '/resources/cbu/life-circle-index/images/thumbnail-placeholder-01.jpg',
      title: '17 Again',
      description: '從遠傳生活圈購買享9折，並贈送一份好禮。',
      link: '#',
    },
    {
      subtitle: '',
      image: '/resources/cbu/life-circle-index/images/thumbnail-placeholder-01.jpg',
      title: 'Toosie Slide',
      description: 'Drake',
      link: '#',
    },
    {
      subtitle: '',
      image: '/resources/cbu/life-circle-index/images/thumbnail-placeholder-01.jpg',
      title: '17 Again',
      description: '從遠傳生活圈購買享9折，並贈送一份好禮。',
      link: '#',
    },
    {
      subtitle: '',
      image: '/resources/cbu/life-circle-index/images/thumbnail-placeholder-01.jpg',
      title: 'Toosie Slide',
      description: 'Drake',
      link: '#',
    },
    {
      subtitle: '',
      image: '/resources/cbu/life-circle-index/images/thumbnail-placeholder-01.jpg',
      title: 'Toosie Slide',
      description: 'Drake',
      link: '#',
    },
    {
      subtitle: '',
      image: '/resources/cbu/life-circle-index/images/thumbnail-placeholder-01.jpg',
      title: 'Toosie Slide',
      description: 'Drake',
      link: '#',
    },
  ]
}} />
```

#### Properties

| 名稱     | 屬性   | 選項 | 必填 | 說明 |
| :------- | :----- | :--- | :--- | :--- |
| id       | string |      |      |      |
| subtitle | string |      |      |      |
| title    | string |      |      |      |
| cards    | array  |      |      |      |
| bgStyle  | array  |      |      |      |
| more     | obj    |      |      |      |

```
LifeCircleNewsCarousel.propTypes = {
  id: PropTypes.string,
  subtitle: PropTypes.string,
  title: PropTypes.string,
  cards: PropTypes.arrayOf(
    PropTypes.objectOf(Card)
  ),
  bgStyle: PropTypes.string,
  more: PropTypes.shape({
    text: PropTypes.string,
    link: PropTypes.string
  })
}
```

## LifeCirclePromoCarousel

```
import LifeCirclePromoCarousel from '../../components/partials/card/LifeCirclePromoCarousel';
<LifeCirclePromoCarousel {...{
  title: '顧老顧少的省心方案',
  cards: [
    {
      image: '/resources/cbu/life-circle-slashie/images/plan-thumbnail-04.png',
      title: '199夠用最實在',
      description: '單門號或家電任你選！',
      link: '#',
    },
    {
      image: '/resources/cbu/life-circle-slashie/images/plan-thumbnail-04.png',
      title: '陪孩子一起探索世界',
      description: '學生憑證件可享指定專案再折$1,000優惠',
      link: '#',
    },
    {
      image: '/resources/cbu/life-circle-slashie/images/plan-thumbnail-04.png',
      title: '超省$1.8親子輕鬆講易付卡',
      description: '網內、網外或市話，每分鐘只要$1.8元，怎麼打都划算！',
      link: '#',
    },
    {
      image: '/resources/cbu/life-circle-slashie/images/plan-thumbnail-04.png',
      title: '199夠用最實在',
      description: '單門號或家電任你選！',
      link: '#',
    },
  ]
}} />

```

#### Properties

| 名稱     | 屬性   | 選項 | 必填 | 說明 |
| :------- | :----- | :--- | :--- | :--- |
| id       | string |      |      |      |
| subtitle | string |      |      |      |
| title    | string |      |      |      |
| cards    | array  |      |      |      |
| bgStyle  | array  |      |      |      |
| more     | obj    |      |      |      |

```
LifeCirclePromoCarousel.propTypes = {
  id: PropTypes.string,
  subtitle: PropTypes.string,
  title: PropTypes.string,
  cards: PropTypes.arrayOf(
    PropTypes.objectOf(Card)
  ),
  bgStyle: PropTypes.string,
  more: PropTypes.shape({
    text: PropTypes.string,
    link: PropTypes.string
  })
}

```

## LifeCircleSongsCarousel

```
import LifeCircleSongsCarousel from '../../components/partials/card/LifeCircleSongsCarousel';
<LifeCircleSongsCarousel {...{
  title: '點聽韓語榜',
  cards: [
    {
      image: '/resources/cbu/life-circle-drama/images/friday-music-thumb-01.jpg',
      title: '這份愛 (This Love)',
      album: '太陽的後裔 韓劇原聲帶',
      signer: 'DAVICHI ',
      action: {
        text: '試聽',
        link: '#',
      },
    },
    {
      image: '/resources/cbu/life-circle-drama/images/friday-music-thumb-01.jpg',
      title: 'Our Story',
      album: '十八歲的瞬間 韓劇原聲帶',
      signer: '邕聖祐 ',
      action: {
        text: '試聽',
        link: '#',
      },
    },
    {
      image: '/resources/cbu/life-circle-drama/images/friday-music-thumb-01.jpg',
      title: 'Love',
      album: '你也是人類嗎？ 韓劇原聲帶',
      signer: 'LYn ',
      action: {
        text: '試聽',
        link: '#',
      },
    },
    {
      image: '/resources/cbu/life-circle-drama/images/friday-music-thumb-01.jpg',
      title: 'You’re My Graden',
      album: '大力女子都奉順 韓劇原聲帶',
      signer: '鄭恩地 ',
      action: {
        text: '試聽',
        link: '#',
      },
    },
    {
      image: '/resources/cbu/life-circle-drama/images/friday-music-thumb-01.jpg',
      title: '這份愛 (This Love)',
      album: '太陽的後裔 韓劇原聲帶',
      signer: 'DAVICHI ',
      action: {
        text: '試聽',
        link: '#',
      },
    },
    {
      image: '/resources/cbu/life-circle-drama/images/friday-music-thumb-01.jpg',
      title: 'Our Story',
      album: '十八歲的瞬間 韓劇原聲帶',
      signer: '邕聖祐 ',
      action: {
        text: '試聽',
        link: '#',
      },
    },
    {
      image: '/resources/cbu/life-circle-drama/images/friday-music-thumb-01.jpg',
      title: 'Love',
      album: '你也是人類嗎？ 韓劇原聲帶',
      signer: 'LYn ',
      action: {
        text: '試聽',
        link: '#',
      },
    },
    {
      image: '/resources/cbu/life-circle-drama/images/friday-music-thumb-01.jpg',
      title: 'You’re My Graden',
      album: '大力女子都奉順 韓劇原聲帶',
      signer: '鄭恩地 ',
      action: '試聽',
      link: '#',
    },
    {
      image: '/resources/cbu/life-circle-drama/images/friday-music-thumb-01.jpg',
      title: '這份愛 (This Love)',
      album: '太陽的後裔 韓劇原聲帶',
      signer: 'DAVICHI ',
      action: {
        text: '試聽',
        link: '#',
      },
    },
    {
      image: '/resources/cbu/life-circle-drama/images/friday-music-thumb-01.jpg',
      title: 'Our Story',
      album: '十八歲的瞬間 韓劇原聲帶',
      signer: '邕聖祐 ',
      action: {
        text: '試聽',
        link: '#',
      },
    },
    {
      image: '/resources/cbu/life-circle-drama/images/friday-music-thumb-01.jpg',
      title: 'Love',
      album: '你也是人類嗎？ 韓劇原聲帶',
      signer: 'LYn ',
      action: {
        text: '試聽',
        link: '#',
      },
    },
    {
      image: '/resources/cbu/life-circle-drama/images/friday-music-thumb-01.jpg',
      title: 'You’re My Graden',
      album: '大力女子都奉順 韓劇原聲帶',
      signer: '鄭恩地 ',
      action: {
        text: '試聽',
        link: '#',
      },
    },
  ]
}} />
```

#### Properties

| 名稱    | 屬性   | 選項 | 必填 | 說明 |
| :------ | :----- | :--- | :--- | :--- |
| id      | string |      |      |      |
| title   | string |      |      |      |
| album   | string |      |      |      |
| signer  | string |      |      |      |
| cards   | array  |      |      |      |
| bgStyle | array  |      |      |      |
| more    | obj    |      |      |      |

```
LifeCircleSongsCarousel.propTypes = {
  id: PropTypes.string,
  title: PropTypes.string,
  album: PropTypes.string,
  signer: PropTypes.string,
  cards: PropTypes.arrayOf(
    PropTypes.objectOf(Card)
  ),
  bgStyle: PropTypes.string,
  more: PropTypes.shape({
    text: PropTypes.string,
    link: PropTypes.string
  })
}
```

## OrderPaper

```
import OrderPaper from '../../components/partials/card/OrderPaper'
<OrderPaper
  list={...[
        {
          productName: 'Samsung Galaxy S9 128GB',
          description: '資費方案：遠傳正職員工們好4G續約活動_新絕配999',
          id: 'TL18000000000',
          timeStamp: '2019/12/31 09:26',
          orderStatus: '資料確認中',
          link: '#',
          linkTarget: '_blank',
          img: '/resources/cbu/img/bitmap-copy@2x.png',
          imgAlt: 'phone',
          arr: ['商品成立', '資料確認中', '出貨準備中', '物流配送中', '已簽收', '門號已開通']
        },
        {
          productName: 'Apple iPad Pro 11 LTE 256GB (2018)',
          description: '資費方案：智慧手機及平板福利品專案_新絕配999',
          id: 'TL18000000001',
          timeStamp: '2019/12/31 09:26',
          orderStatus: '商品成立',
          linkTarget: '_blank',
          link: '#',
          imgAlt: 'phone',
          img: '/resources/cbu/img/rectangle@2x.png',
          arr: ['商品成立', '資料確認中', '出貨準備中', '物流配送中', '已簽收', '門號已開通']
        },
      ]}
  key={list.id}
/>
```

#### Properties

| 名稱 | 屬性  | 選項 | 必填 | 說明 |
| :--- | :---- | :--- | :--- | :--- |
| list | array |      |      |      |
```
OrderPaper.propTypes = {
    list: PropTypes.shape({
        productName: PropTypes.string,
        description: PropTypes.string,
        id: PropTypes.string,
        timeStampid: PropTypes.string,
        orderStatus: PropTypes.string,
        link: PropTypes.string,
        linkTarget: PropTypes.string,
        img: PropTypes.string,
        imgAlt: PropTypes.string,
        arr: PropTypes.array,
    })
}
```

## PlanCard

```
import PlanCard from '../../components/partials/card/PlanCard';
<PlanCard
  title="$149資費優惠"
  cards={[
    {
      "type": "default",
      "ribbon": "單辦門號",
      "image": "/resources/cbu/exclusive/estore-exclusive-plan-icon-01@2x.png",
      "title": "月付149 雙飽只給我的飽",
      "list": [
        {
          "text": "滑Line、FB流量充足"
        },
        {
          "text": "網內無限通話",
          "tooltip": "網內無限通話"
        }
      ],
      "action": {
        "btnStyle": "primary",
        "text": "立即申辦",
        "link": "#",
        "target": "_self"
      }
    },
    {
      "type": "default",
      "ribbon": "單辦門號",
      "image": "/resources/cbu/exclusive/estore-exclusive-plan-icon-02@2x.png",
      "title": "月付298 雙倍升級 週末全速飽",
      "list": [
        {
          "text": "週六日全速上網吃到飽"
        },
        {
          "text": "網內無限通話"
        }
      ],
      "action": {
        "btnStyle": "primary",
        "text": "立即申辦",
        "link": "#",
        "target": "_self"
      }
    },
    {
      "type": "promotion",
      "title": "老客戶請看這，續約好禮很多種，登入後看更多！",
      "action": {
        "btnStyle": "primary",
        "text": "馬上登入",
        "link": "#",
        "target": "_self"
      }
  }]} 
/>
```

#### Properties

| 名稱      | 屬性   | 選項 | 必填 | 說明 |
| :-------- | :----- | :--- | :--- | :--- |
| title     | string |      |      |      |
| cards     | array  |      |      |      |
| openModal | func   |      |      |      |


```
PlanCard.propTypes = {
  title: PropTypes.string,
  cards: PropTypes.arrayOf(
    PropTypes.shape({
      ribbon: PropTypes.string,
      image: PropTypes.string,
      title: PropTypes.string,
      list: PropTypes.arrayOf(
        PropTypes.shape({
          text: PropTypes.string,
          tooltip: PropTypes.string,
        })
      ),
      action: PropTypes.shape({
        text: PropTypes.string,
        link: PropTypes.string,
        target: PropTypes.string,
      }),
    })
  ),
  openModal: PropTypes.func,
};
```

## SectionCarousel1

```
import SectionCarousel1 from '../../components/partials/card/SectionCarousel1';
<SectionCarousel1 {...{
  title: '你的專屬優惠',
  cards: [
    {
      image: '/resources/cbu/e-service/images/image-cbu-discount-video-16x9.png',
      title: '本月影片免費看!',
      description: '話題電影、日劇、韓劇等等應有盡有',
      link: '#',
    },
    {
      image: '/resources/cbu/e-service/images/image-cbu-discount-eat-16x9.png',
      title: '中午不知道吃什麼？',
      description: 'Uber Eats 送遠傳新客優惠金200元',
      link: '#',
    },
    {
      image: '/resources/cbu/e-service/images/image-cbu-discount-travel-16x9.png',
      title: '連假打算出國？',
      description: '遠遊卡吃到飽上網不再煩惱用量 ',
      link: '#',
    },
    {
      image: '/resources/cbu/e-service/images/image-cbu-discount-video-16x9.png',
      title: '本月影片免費看!',
      description: '話題電影、日劇、韓劇等等應有盡有',
      link: '#',
    },
  ]
}} />
```

#### Properties

| 名稱                    | 屬性   | 選項 | 必填 | 說明                    |
| :---------------------- | :----- | :--- | :--- | :---------------------- |
| title                   | string |      |      |                         |
| cards                   | array  |      |      |                         |
| bgStyle                 | string |      |      |                         |
| more                    | obj    |      |      | text: PropTypes.string, |
| link: PropTypes.string, |

```
SectionCarousel1.propTypes = {
  title: PropTypes.string,
  cards: PropTypes.array,
  bgStyle: PropTypes.string,
  more: PropTypes.shape({
    text: PropTypes.string,
    link: PropTypes.string,
  }),
};
```

## SectionProductTab

```
import SectionProductTab from '../../components/partials/card/SectionProductTab'
<SectionProductTab {...{
  title: '本週最熱門',
  more: {
    text: '看更多',
    link: '/',
  },
  tabs: {
    name: 'promo-product-tab',
    default: 0,
    list: [
      {label: 'iPhone手機'},
      {label: 'Android手機'},
      {label: '穿戴裝置'},
      {label: '拆封機'},
      {label: '配件'},
    ]
  },
  tabContent: [
    [
      {
        image: '/resources/cbu/estore/estore-product-thumb-01@2x.jpg',
        ribbon: '網路限定優惠',
        meta: 'Apple',
        title: 'iPhone 11 Pro Max 256GB',
        tag: '5G手機',
        salePrice: '$41,400',
        projectPrice: '$10,500',
        originPrice: '$45,400',
      },
      {
        image: '/resources/cbu/estore/estore-product-thumb-02@2x.jpg',
        meta: 'Apple',
        title: 'iPhone 11 Pro Max 128GB',
        tag: '福利A品',
        salePrice: '$1,399',
        projectPrice: '$10,500',
      },
      {
        image: '/resources/cbu/estore/estore-product-thumb-02@2x.jpg',
        meta: 'Apple',
        title: 'iPhone 11 Pro Max 256GB',
        tag: '5G手機',
        salePrice: '$41,400',
        projectPrice: '$10,500',
      },
      {
        image: '/resources/cbu/estore/estore-product-thumb-01@2x.jpg',
        meta: 'Apple',
        title: 'iPhone 11 Pro Max 256GB',
        tag: '5G手機',
        salePrice: '$41,400',
        projectPrice: '$10,500',
      },
    ]
  ]
}} />
```

#### Properties

| 名稱       | 屬性   | 選項 | 必填 | 說明 |
| :--------- | :----- | :--- | :--- | :--- |
| title      | string |      |      |      |
| more       | obj    |      |      |      |
| tabs       | obj    |      |      |      |
| tabContent | array  |      |      |      |
```
SectionProductTab.propTypes = {
  title: PropTypes.string,
  more: PropTypes.shape({
    text: PropTypes.string,
    link: PropTypes.string,
    target: PropTypes.string
  }),
  tabs: PropTypes.shape({
    name: PropTypes.string,
    default: PropTypes.number,
    list: PropTypes.arrayOf(
      PropTypes.shape({
        label: PropTypes.string
      })
    )
  }),
  tabContent: PropTypes.arrayOf(
    PropTypes.arrayOf(
      PropTypes.shape({
        link: PropTypes.string,
        target: PropTypes.string,
        image: PropTypes.string,
        ribbon: PropTypes.string,
        tag: PropTypes.string,
        meta: PropTypes.string,
        title: PropTypes.string,
        originalPrice: PropTypes.string,
        projectPrice: PropTypes.string,
        salePrice: PropTypes.string,
      })
    )
  )
}
```

## SectionRoamingProductCardCarousel

```
import SectionRoamingProductCardCarousel from '../../components/partials/card/SectionRoamingProductCardCarousel';
<SectionRoamingProductCardCarousel
  {...{
  title: '',
  cards: [
    {
      tag: {
        color: 'red',
        text: '網路限定優惠',
      },
      image: '/resources/cbu/roaming/card-sim-7-days-499@2x.jpg',
      title: '日本 7日5GB高速上網',
      lists: [
        { text: '每日不到 $100 不降速吃到飽' },
        { text: '可連續使用 168 小時' },
        { text: '使用日本 KDDI (AU) 網路' },
      ],
      action: {
        text: '前往購買',
        link: '/',
      },
    },
    {
      tag: {
        color: '',
        text: '',
      },
      title: '韓國 5日上網吃到飽',
      image: '/resources/cbu/roaming/card-sim-5-days-599@2x.jpg',
      lists: [
        { text: '每日不到 $100 不降速吃到飽' },
        { text: '可連續使用 168 小時' },
        { text: '使用韓國 KDDI (AU) 網路' },
      ],
      action: {
        text: '前往購買',
        link: '#',
      },
    },
    {
      tag: {
        color: '',
        text: '',
      },
      title: '日本 7日5GB高速上網',
      image: '/resources/cbu/roaming/card-sim-7-days-759@2x.jpg',
      lists: [
        { text: '每日不到 $100 不降速吃到飽' },
        { text: '可連續使用 168 小時' },
        { text: '使用日本 KDDI (AU) 網路' },
      ],
      action: {
        text: '前往購買',
        link: '/',
      },
    },
    {
      tag: {
        color: '',
        text: '',
      },
      title: '日本 7日5GB高速上網',
      image: '/resources/cbu/roaming/card-sim-5-days-599@2x.jpg',
      lists: [
        { text: '每日不到 $100 不降速吃到飽' },
        { text: '可連續使用 168 小時' },
        { text: '使用日本 KDDI (AU) 網路' },
      ],
      action: {
        text: '前往購買',
        link: '/',
      },
    },
  ],
}}
/>

#### Properties

| 名稱  | 屬性   | 選項 | 必填 | 說明 |
| :---- | :----- | :--- | :--- | :--- |
| title | string |      |      |      |
| card  | array  |      |      |      |

```

## ServiceEntry

```
import ServiceEntry from '../../components/partials/card/ServiceEntry'
<ServiceEntry {...{
  title: '線上申辦',
  cards: [
    {
      title: '企業行動優惠',
      link: '#',
    },
    {
      title: '手機保險',
      link: '#',
    },
    {
      title: '大寬頻企業光纖',
      link: '#',
    },
    {
      title: 'Wifi 上網',
      link: '#',
    },
  ],
}} />
```

#### Properties

| 名稱  | 屬性   | 選項 | 必填 | 說明 |
| :---- | :----- | :--- | :--- | :--- |
| title | string |      |      |      |
| card  | array  |      |      |      |

```
ServiceEntry.propTypes = {
    title: PropTypes.string,
    cards: PropTypes.arrayOf(
        PropTypes.shape({
            title: PropTypes.string,
            link: PropTypes.string
        })
    )
}
```

## SwitchCard

```
import SwitchCard from '../../components/partials/card/SwitchCard'
<SwitchCard {...{
  title: '漫遊通話設定',
  icon: '/resources/cbu//help-center/images/information-gray.svg',
  description: '申請漫遊上網後請保持開啟，以確保接收漫遊通知簡訊',
  tips: 'Tips Tips Tips Tips Tips',
  switch: [
    {
      on: '關閉',
      off: '開啟',
    },
    
  ]
}} />
```

#### Properties

| 名稱       | 屬性   | 選項 | 必填 | 說明 |
| :--------- | :----- | :--- | :--- | :--- |
| title         | string |      |      |      |
| description      | string |      |      |      |
| className      | string |      |      |      |
| icon      | string |      |      |      |
| switch      | array |      |      |      |

```
SwitchCard.propTypes = {
  title: PropTypes.string,
  description: PropTypes.string,
  className: PropTypes.string,
  icon: PropTypes.string,
  switch: PropTypes.arrayOf(
    PropTypes.shape({
      on: PropTypes.string,
      off: PropTypes.string,
    })
  ),
};
```

## WithIconCard

```
import WithIconCard from '../../components/partials/card/WithIconCard';
<WithIconCard {...{
  title: '<h2>其他漫遊</h2>',
  // more: {
  //   link: '#',
  //   text: '更多話題',
  // },
  cards: [
    {
      image: '/resources/cbu/roaming/airplane.svg',
      subtitle: '',
      title: '機上漫遊',
      description:
        '搭飛機也能上網滑手機！上網、追劇、遠端辦公、聊 Line，在二萬英呎高空上一點也不無聊！輕鬆體驗在高空飆網的樂趣！',
      link: '#',
    },
    {
      image: '/resources/cbu/roaming/wifi.svg',
      subtitle: '',
      title: 'Wifi優惠費率',
      description:
        '搭飛機也能上網滑手機！上網、追劇、遠端辦公、聊 Line，在二萬英呎高空上一點也不無聊！輕鬆體驗在高空飆網的樂趣...',
      link: '#',
    },
  ],
}} />
```

#### Properties

| 名稱       | 屬性   | 選項 | 必填 | 說明 |
| :--------- | :----- | :--- | :--- | :--- |
|title         | string |      |      |      |
| card       | array |      |      |      |

```
WithIconCard.propTypes = {
  title: PropTypes.string,
  cards: PropTypes.arrayOf(
    PropTypes.shape({
      image: PropTypes.string,
      retinaImage: PropTypes.string,
      title: PropTypes.string,
      description: PropTypes.string,
      link: PropTypes.string,
      target: PropTypes.string, // _self || _blank
    })
  ),
};

```