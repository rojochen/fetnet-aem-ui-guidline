# carousel

## BrandCarousel

```
import BrandCarousel from '../../components/partials/carousel/BrandCarousel';
<BrandCarousel id="hiring" partner={[
        {
          id: '1',
          content: [
            {
              url: '/resources/cbu/img/partner-logo-1@2x.png',
              alt: 'img'
            },
            {
              url: '/resources/cbu/img/partner-logo-2@2x.png',
              alt: 'img'
            },
            {
              url: '/resources/cbu/img/partner-logo-3@2x.png',
              alt: 'img'
            },
            {
              url: '/resources/cbu/img/partner-logo-4@2x.png',
              alt: 'img'
            },
            {
              url: '/resources/cbu/img/partner-logo-5@2x.png',
              alt: 'img'
            },
            {
              url: '/resources/cbu/img/partner-logo-6@2x.png',
              alt: 'img'
            },
          ],
        },
        {
          id: '2',
          content: [
            {
              url: '/resources/cbu/img/partner-logo-1@2x.png',
              alt: 'img'
            },
            {
              url: '/resources/cbu/img/partner-logo-2@2x.png',
              alt: 'img'
            },
            {
              url: '/resources/cbu/img/partner-logo-3@2x.png',
              alt: 'img'
            },
            {
              url: '/resources/cbu/img/partner-logo-4@2x.png',
              alt: 'img'
            },
            {
              url: '/resources/cbu/img/partner-logo-5@2x.png',
              alt: 'img'
            },
            {
              url: '/resources/cbu/img/partner-logo-6@2x.png',
              alt: 'img'
            },
          ],
        },
        {
          id: '3',
          content: [
            {
              url: '/resources/cbu/img/partner-logo-1@2x.png',
              alt: 'img'
            },
            {
              url: '/resources/cbu/img/partner-logo-2@2x.png',
              alt: 'img'
            },
            {
              url: '/resources/cbu/img/partner-logo-3@2x.png',
              alt: 'img'
            },
            {
              url: '/resources/cbu/img/partner-logo-4@2x.png',
              alt: 'img'
            },
            {
              url: '/resources/cbu/img/partner-logo-5@2x.png',
              alt: 'img'
            },
            {
              url: '/resources/cbu/img/partner-logo-6@2x.png',
              alt: 'img'
            },
          ],
        },
        {
          id: '4',
          content: [
            {
              url: '/resources/cbu/img/partner-logo-1@2x.png',
              alt: 'img'
            },
            {
              url: '/resources/cbu/img/partner-logo-2@2x.png',
              alt: 'img'
            },
            {
              url: '/resources/cbu/img/partner-logo-3@2x.png',
              alt: 'img'
            },
            {
              url: '/resources/cbu/img/partner-logo-4@2x.png',
              alt: 'img'
            },
            {
              url: '/resources/cbu/img/partner-logo-5@2x.png',
              alt: 'img'
            },
            {
              url: '/resources/cbu/img/partner-logo-6@2x.png',
              alt: 'img'
            },
          ],
        },
      ]} />
```

#### Properties

| 名稱    | 屬性   | 選項 | 必填 | 說明 |
| :------ | :----- | :--- | :--- | :--- |
| id      | string |      |      |      |
| partner | array  |      |      |      |

```
BrandCarousel.propTypes = {
  id: PropTypes.string,
  partner: PropTypes.arrayOf(
    PropTypes.shape({
      id: PropTypes.string,
      content: PropTypes.array
    })
  )
}
```

## CarouselBanner3

```
import CarouselBanner3 from '../components/partials/carousel/CarouselBanner3';
<CarouselBanner3 slider={[
  {
    type: '限時特惠中',
    title: '<h2>4.5G方案最低199 更快網速</h2>',
    img: {
      md: '/resources/cbu/discount/baby-1920x470-KV.jpg',
      sm: '/resources/cbu/discount/baby-750x660.jpg',
    },
    action: {
      text: '馬上申辦',
      link: '#',
    },
  },
  {
    type: '限時特惠中',
    title: '<h2>4.5G方案最低199 更快網速</h2>',
    img: {
      md: '/resources/cbu/discount/cbu-4.5G-1920x360.jpg',
      sm: '/resources/cbu/discount/cbu-4.5g-750x640.jpg',
    },
    action: {
      text: '馬上申辦',
      link: '#',
    },
  },
  {
    type: '限時特惠中',
    title: '<h2>4.5G方案最低199 更快網速</h2>',
    img: {
      md: '/resources/cbu/discount/cbu-4.5G-1920x360.jpg',
      sm: '/resources/cbu/discount/cbu-4.5g-750x640.jpg',
    },
    action: {
      text: '馬上申辦',
      link: '#',
    },
  },
  {
    id: '004',
    type: '頭家輕鬆配系列產品',
    title: '<h2>市內電話輕鬆省</h2>',
    img: {
      md: '/resources/cbu/discount/cbu-4.5G-1920x360.jpg',
      sm: '/resources/cbu/discount/cbu-4.5g-750x640.jpg',
    },
    action: {
      text: '馬上申辦',
      link: '#',
    },
  },
]} />
```

#### Properties

| 名稱   | 屬性  | 選項 | 必填 | 說明 |
| :----- | :---- | :--- | :--- | :--- |
| slider | array |      |      |      |

```
CarouselBanner3.propTypes = {
  slider: PropTypes.arrayOf(
    PropTypes.shape({
      img: PropTypes.shape({
        md: PropTypes.string,
        sm: PropTypes.string,
      }).isRequired,
      type: PropTypes.string.isRequired,
      title: PropTypes.string.isRequired,
      action: PropTypes.shape({
        text: PropTypes.string.isRequired,
        link: PropTypes.string.isRequired,
      }),
    })
  ),
};

```

## CarouselWithTag

```
import CarouselWithTag from '../../components/partials/carousel/CarouselWithTag'
<CarouselWithTag
  title={this.props.carousel.title}
  cards={this.props.carousel.cards}
  id={this.props.carousel.id}
/>
```

#### Properties

| 名稱  | 屬性   | 選項 | 必填 | 說明 |
| :---- | :----- | :--- | :--- | :--- |
| title | string |      |      |      |
| id    | string |      |      |      |
| cards | array  |      |      |      |

## LifeCircleIndexAdCarousel

```
import LifeCircleIndexAdCarousel from '../../components/partials/carousel/LifeCircleIndexAdCarousel';
<LifeCircleIndexAdCarousel {...{
  slider: [
    {
      image: '/resources/cbu/life-circle-index/images/img-soyummy-480-x-240.jpg',
      title: 'SoYummy 手壓蜜',
      price: '200 + 50元',
      action: {
        text: '立即兌換',
        link: '#',
      },
    },
    {
      image: '/resources/cbu/life-circle-index/images/img-soyummy-480-x-240.jpg',
      title: 'SoYummy 手壓蜜',
      price: '200 + 50元',
      action: {
        text: '立即兌換',
        link: '#',
      },
    },
    {
      image: '/resources/cbu/life-circle-index/images/img-soyummy-480-x-240.jpg',
      title: 'SoYummy 手壓蜜',
      price: '200 + 50元',
      action: {
        text: '立即兌換',
        link: '#',
      },
    },
    {
      image: '/resources/cbu/life-circle-index/images/img-soyummy-480-x-240.jpg',
      title: 'SoYummy 手壓蜜',
      price: '200 + 50元',
      action: {
        text: '立即兌換',
        link: '#',
      },
    },
  ],
}} />
```

#### Properties

| 名稱   | 屬性  | 選項 | 必填 | 說明 |
| :----- | :---- | :--- | :--- | :--- |
| slider | array |      |      |      |

```
LifeCircleIndexAdCarousel.propTypes = {
  slider: PropTypes.arrayOf(
    PropTypes.shape({
      image: PropTypes.string.isRequired,
      title: PropTypes.string.isRequired,
      price: PropTypes.string.isRequired,
      action: PropTypes.shape({
        text: PropTypes.string.isRequired,
        link: PropTypes.string.isRequired
      }),
      'tracking-prefix': PropTypes.string
    })
  )
}
```

## LifeCircleIndexMainCarousel

```
import LifeCircleIndexMainCarousel from '../../components/partials/carousel/LifeCircleIndexMainCarousel';
<LifeCircleIndexMainCarousel {...{
  slider: [
    {
      theme: 'dark',
      image: '/resources/cbu/life-circle-index/images/cbu-lifecircle-article-kv01.jpg',
      imageMb: '/resources/cbu/life-circle-index/images/img-soyummy-480-x-240@2x.jpg',
      title: '居家必備的吸塵器1',
      description: '以CP值破表的稱號，熱銷全台超過4,000台、集資金額超過3,600萬台幣，而引起熱議...',
      isLast: false,
      action: {
        text: '體驗故事',
        link: '#',
      },
    },
    {
      // theme: 'dark',
      image: '/resources/cbu/life-circle-index/images/cbu-lifecircle-article-kv01.jpg',
      title: '居家必備的吸塵器2',
      description: '以CP值破表的稱號，熱銷全台超過4,000台、集資金額超過3,600萬台幣，而引起熱議...',
      isLast: false,
      action: {
        text: '體驗故事',
        link: '#',
      },
    },
    {
      image: '/resources/cbu/life-circle-index/images/cbu-lifecircle-article-kv01.jpg',
      title: '居家必備的吸塵器3',
      description: '以CP值破表的稱號，熱銷全台超過4,000台、集資金額超過3,600萬台幣，而引起熱議...',
      action: {
        text: '體驗故事',
        link: '#',
      },
    },
    {
      image: '/resources/cbu/life-circle-index/images/cbu-lifecircle-article-kv01.jpg',
      title: '居家必備的吸塵器4',
      description: '以CP值破表的稱號，熱銷全台超過4,000台、集資金額超過3,600萬台幣，而引起熱議...',
      isLast: false,
      action: {
        text: '體驗故事',
        link: '#',
      },
    },
    {
      image: '/resources/cbu/life-circle-index/images/cbu-lifecircle-article-kv01.jpg',
      title: '居家必備的吸塵器5',
      description: '以CP值破表的稱號，熱銷全台超過4,000台、集資金額超過3,600萬台幣，而引起熱議...',
      isLast: false,
      action: {
        text: '體驗故事',
        link: '#',
      },
    },
    {
      image: '/resources/cbu/life-circle-index/images/cbu-lifecircle-article-kv01.jpg',
      title: '居家必備的吸塵器6',
      description: '以CP值破表的稱號，熱銷全台超過4,000台、集資金額超過3,600萬台幣，而引起熱議...',
      isLast: false,
      action: {
        text: '體驗故事',
        link: '#',
      },
    },
    {
      image: '/resources/cbu/life-circle-index/images/cbu-lifecircle-article-kv01.jpg',
      title: '居家必備的吸塵器7',
      description: '以CP值破表的稱號，熱銷全台超過4,000台、集資金額超過3,600萬台幣，而引起熱議...',
      action: {
        text: '體驗故事',
        link: '#',
      },
    },
    {
      image: '/resources/cbu/life-circle-index/images/cbu-lifecircle-article-kv01.jpg',
      title: '居家必備的吸塵器8',
      description: '以CP值破表的稱號，熱銷全台超過4,000台、集資金額超過3,600萬台幣，而引起熱議...',
      isLast: false,
      action: {
        text: '體驗故事',
        link: '#',
      },
    },
    {
      image: '/resources/cbu/life-circle-index/images/cbu-lifecircle-article-kv01.jpg',
      title: '居家必備的吸塵器9',
      description: '以CP值破表的稱號，熱銷全台超過4,000台、集資金額超過3,600萬台幣，而引起熱議...',
      isLast: false,
      action: {
        text: '體驗故事',
        link: '#',
      },
    },
    {
      image: '/resources/cbu/life-circle-index/images/cbu-lifecircle-article-kv01.jpg',
      title: '更多策展',
      description: '',
      isLast: true,
      action: {
        text: '更多策展',
        link: '#',
      },
    },
  ],
}} />
```

#### Properties

| 名稱   | 屬性  | 選項 | 必填 | 說明 |
| :----- | :---- | :--- | :--- | :--- |
| slider | array |      |      |      |

```
LifeCircleIndexMainCarousel.propTypes = {
  slider: PropTypes.arrayOf(
    PropTypes.shape({
      theme: PropTypes.string, // light or dark
      image: PropTypes.string.isRequired,
      alt: PropTypes.string,
      title: PropTypes.string.isRequired,
      isLast: PropTypes.bool,
      action: PropTypes.shape({
        text: PropTypes.string.isRequired,
        link: PropTypes.string.isRequired,
        target: PropTypes.string,
      }),
      trackingPrefix: PropTypes.string,
      position: PropTypes.number,
    })
  ),
};

```

## LifeCirclePromotion

```
import LifeCirclePromotion from '../components/partials/carousel/LifeCirclePromotion'
<LifeCirclePromotion {...{
  title: '享受你的生活圈',
  slider: [
    {
      image: {
        md: '/resources/cbu/cbu-index/home-1-1200-x-430.jpg',
        sm: '/resources/cbu/cbu-index/home-1-330-x-360.jpg'
      },
      alt: '',
      title: '追劇人生',
      description: '追劇讓我暫時脫離現實，體驗 1% 極致的美好人生。',
      action: {
        text: '看更多追劇故事',
        link: '#',
        target: '_self',
      },
      icons: [
        {
          link: '#',
          img: '/resources/cbu/cbu-index/friday-shopping-1@2x.png',
          alt: '金泰熙著裝',
          text: '金泰熙著裝',
          description: 'friDay購物'
        },
        {
          link: '#',
          img: '/resources/cbu/cbu-index/friday-57@2x.png',
          alt: '懶人記帳本',
          text: '懶人記帳本',
          description: 'friDay 57'
        },
        {
          link: '#',
          img: '/resources/cbu/cbu-index/friday-music@2x.png',
          alt: '必聽的梨泰院',
          text: '必聽的梨泰院',
          description: 'friDay 音樂'
        },
        {
          link: '#',
          img: '/resources/cbu/cbu-index/friday-photo@2x.png',
          alt: '保存甜蜜回憶',
          text: '保存甜蜜回憶',
          description: 'friDay相片書'
        },
        {
          link: '#',
          img: '/resources/cbu/cbu-index/laundry@2x.png',
          alt: '幫你洗衣服',
          text: '幫你洗衣服',
          description: '潔衣家洗衣服務'
        },
        {
          link: '#',
          img: '/resources/cbu/cbu-index/flight@2x.png',
          alt: '出國上網',
          text: '出國上網',
          description: '遠遊卡'
        },
        {
          link: '#',
          img: '/resources/cbu/cbu-index/flight-video@2x.png',
          alt: '直播新聞',
          text: '直播新聞',
          description: 'friDay影音'
        },
      ]
    },
    {
      image: {
        md: '/resources/cbu/cbu-index/home-2-1200-x-430.jpg',
        sm: '/resources/cbu/cbu-index/home-2-330-x-360.jpg'
      },
      alt: '',
      title: '斜槓老爸',
      description: '不用當超人，當個懂得生活的斜槓老爸。',
      action: {
        text: '看更多斜槓老爸',
        link: '#',
        target: '_self',
      },
      icons: [
        {
          link: '#',
          img: '/resources/cbu/cbu-index/friday-shopping-1@2x.png',
          alt: '金泰熙著裝',
          text: '金泰熙著裝',
          description: 'friDay購物'
        },
        {
          link: '#',
          img: '/resources/cbu/cbu-index/friday-57@2x.png',
          alt: '懶人記帳本',
          text: '懶人記帳本',
          description: 'friDay 57'
        },
        {
          link: '#',
          img: '/resources/cbu/cbu-index/friday-music@2x.png',
          alt: '必聽的梨泰院',
          text: '必聽的梨泰院',
          description: 'friDay 音樂'
        },
        {
          link: '#',
          img: '/resources/cbu/cbu-index/friday-photo@2x.png',
          alt: '保存甜蜜回憶',
          text: '保存甜蜜回憶',
          description: 'friDay相片書'
        },
        {
          link: '#',
          img: '/resources/cbu/cbu-index/laundry@2x.png',
          alt: '幫你洗衣服',
          text: '幫你洗衣服',
          description: '潔衣家洗衣服務'
        },
        {
          link: '#',
          img: '/resources/cbu/cbu-index/flight@2x.png',
          alt: '出國上網',
          text: '出國上網',
          description: '遠遊卡'
        },
        {
          link: '#',
          img: '/resources/cbu/cbu-index/flight-video@2x.png',
          alt: '直播新聞',
          text: '直播新聞',
          description: 'friDay影音'
        },
      ]
    },
  ]
}} />
```

#### Properties

| 名稱   | 屬性   | 選項 | 必填 | 說明 |
| :----- | :----- | :--- | :--- | :--- |
| title  | string |      |      |      |
| slider | array  |      |      |      |

```
LifeCirclePromotion.propTypes = {
  title: PropTypes.string,
  slider: PropTypes.arrayOf(
    PropTypes.shape({
      image: PropTypes.shape({
        md: PropTypes.string,
        sm: PropTypes.string,
      }),
      alt: PropTypes.string,
      title: PropTypes.string,
      description: PropTypes.string,
      action: PropTypes.shape({
        text: PropTypes.string,
        link: PropTypes.string,
        target: PropTypes.string,
      }),
      icons: PropTypes.arrayOf(
        PropTypes.shape({
          img: PropTypes.string,
          alt: PropTypes.string,
          title: PropTypes.string,
          description: PropTypes.string,
          target: PropTypes.string,
          link: PropTypes.string,
        })
      ),
    })
  ),
};

```

## ToolsItemCarousel

```
import ToolsItemCarousel from '../../components/partials/carousel/ToolsItemCarousel';
<ToolsItemCarousel {...{
  title: '不再為了帳單而擔心',
  className: 'pb-0 mt-4',
  item: [
    {
      image: '/resources/cbu/life-circle-slashie/images/flight-video.svg',
      title: 'Google Play 代收',
      // description: 'friDay影音',
    },
    {
      image: '/resources/cbu/life-circle-slashie/images/smart-speaker.svg',
      title: 'iTines 代收',
      // description: '愛講語音助理',
    },
    {
      image: '/resources/cbu/life-circle-slashie/images/bobee-parking.svg',
      title: 'Microsoft 代收',
      // description: '愛車守護寶',
    },
    {
      image: '/resources/cbu/life-circle-slashie/images/friday-shopping-2.svg',
      title: '小額付費',
      // description: 'friDay購物',
    },
    {
      image: '/resources/cbu/life-circle-slashie/images/laundry.svg',
      title: '停車代收',
      // description: '潔衣家洗衣服務',
    },
    {
      image: '/resources/cbu/life-circle-slashie/images/friday-57.svg',
      title: '代收設定查詢',
      // description: 'friDay 57',
    },
    {
      image: '/resources/cbu/life-circle-slashie/images/3-c-doctor.svg',
      title: '行動代收',
      // description: '數位萬事通',
    }
  ]
}} />
```

#### Properties

| 名稱      | 屬性   | 選項 | 必填 | 說明 |
| :-------- | :----- | :--- | :--- | :--- |
| title     | string |      |      |      |
| className | string |      |      |      |
| item      | obj    |      |      |      |

```
ToolsItemCarousel.propTypes = {
  title: PropTypes.string,
  className: PropTypes.string,
  item: PropTypes.shape({
    img: PropTypes.string,
    alt: PropTypes.string,
    title: PropTypes.string,
    description: PropTypes.string,
    link: PropTypes.string,
    target: PropTypes.string,
  }),
}
```