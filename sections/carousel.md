# Carousel

## SectionCarousel2

組合牌卡的輪播樣式, 超過4項時出現上下則輪播按鈕. 可依需求編輯欄位:

section:   
1. 大標: 最大字符串長度&lt;20 \(20個字元\), 建議最多1行.

牌卡:   
1. 副標: 最大行數&lt;1  
2. 大標: 最大行數&lt;2   
3. 小標: 最大行數&lt;3

{% tabs %}
{% tab title="Web" %}
![](../.gitbook/assets/image%20%28124%29.png)

牌卡超過4項時出現輪播按鈕

![](../.gitbook/assets/image%20%2896%29.png)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/image%20%28167%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Usage" %}
```jsx
import SectionCarousel2 from '../components/partials/card/SectionCarousel2';

<SectionCarousel2
  id='you-might-like'
  bgImage={{
    md: '/resources/ebu/images/ebu-section-bkg-1440x620.jpg',
    sm: '/resources/ebu/images/ebu-section-bkg-1440x620.jpg',
  }}
  title='您可能有興趣...'
  cards={[
    {
      meta: '中小企業解決方案',
      title: '頭家輕鬆省方案',
      description: '遠傳市話推出超優質優惠方案，節省成本同享有優質通話品質！',
      link: '#',
    },
    {
      meta: '中小企業解決方案',
      title: '企業 Office 輕享方案',
      description: '最殺最彈性付費，雲端行動辦公，遠傳一次幫您搞定！',
      link: '#',
    },
    {
      meta: '寬頻上網',
      title: '大寬頻企業光纖',
      description: '企業級高速穩定的網路服務，幫助企業用高效率提升競爭力。',
      link: '#',
    },
    {
      meta: '語音服務',
      title: '網內互打免費優惠',
      description: '不管國內還是國外，行動還是市話，免安裝一次到位。',
      link: '#',
    },
  ]}
/>
```
{% endtab %}

{% tab title="SectionCarousel2.js" %}
```jsx
import React from 'react';
import Slider from 'react-slick';
import { NavLink } from 'react-router-dom';

import Card from '../../card/Card';

import PropTypes from 'prop-types';

const SectionCarouse2 = props => {
  const setting = {
    dots: false,
    infinite: false,
    arrows: true,
    slidesToShow: 4,
    draggable: true,
    responsive: [
      {
        breakpoint: 960,
        settings: {
          arrows: true,
          slidesToShow: 4,
          infinite: true,
          dots: false,
        },
      },
      {
        breakpoint: 768,
        settings: {
          arrows: true,
          slidesToShow: 2,
          variableWidth: true,
        },
      },
      {
        breakpoint: 480,
        settings: {
          arrows: true,
          slidesToShow: 1,
          variableWidth: true,
        },
      },
    ],
  };

  return (
    <section className='fui-horzonal-cards is-narrow' id={props.id}>
      {/* <ArrowLeftWhite/>
            <ArrowRightWhite/> */}
      {props.bgImage ? (
        <div className='bg'>
          <img src={props.bgImage.md} className='bg-image d-none d-md-block' alt={props.bgImage.md} />
          <img src={props.bgImage.sm} className='bg-image d-block d-md-none' alt={props.bgImage.sm} />
        </div>
      ) : (
        ''
      )}
      <div className='fui-container'>
        <h2 className='section-title m-0 p-0'>{props.title}</h2>
        <Slider {...setting} className='horizontal-cards'>
          {props.cards.map((card, idx) => (
            <Card key={idx} {...card} style={{ width: 270 }} />
          ))}
        </Slider>
        {props.more ? (
          <div className='align-center'>
            <NavLink to={props.more.link} className='fui-more'>
              {props.more.text}
              <br />
              <i className='icon-chevron-down'></i>
            </NavLink>
          </div>
        ) : (
          ''
        )}
      </div>
    </section>
  );
};

SectionCarouse2.propTypes = {
  title: PropTypes.string,
  maxCards: PropTypes.number,
  cards: PropTypes.arrayOf(PropTypes.objectOf(Card)),
  bgImage: PropTypes.shape({
    md: PropTypes.string,
    sm: PropTypes.string,
  }),
  more: PropTypes.shape({
    text: PropTypes.string,
    link: PropTypes.string,
  }),
};

export default SectionCarouse2;

```
{% endtab %}
{% endtabs %}

#### Properties

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x540D;&#x7A31;</th>
      <th style="text-align:left">&#x5C6C;&#x6027;</th>
      <th style="text-align:left">&#x5FC5;&#x586B;</th>
      <th style="text-align:left">&#x9078;&#x9805;</th>
      <th style="text-align:left">&#x8AAA;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">id</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x5340;&#x584A;ID&#xFF0C;&#x4F9B; NavAnchor &#x4F7F;&#x7528;</td>
    </tr>
    <tr>
      <td style="text-align:left">bgImage</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>{</p>
        <p>md: string,</p>
        <p>sm: string,</p>
        <p>}</p>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">title</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x6A19;&#x984C;</td>
    </tr>
    <tr>
      <td style="text-align:left">cards</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>{</p>
        <p>meta,</p>
        <p>title
          <br />description
          <br />link</p>
        <p>}</p>
      </td>
      <td style="text-align:left">&#x6B04;&#x4F4D;&#x8ACB;&#x53C3;&#x8003; <a href="https://app.gitbook.com/@ajacreative/s/fetnet-1/~/drafts/-M1UwW6hQrq6o_OTbp_Z/components/card">Card</a>
      </td>
    </tr>
  </tbody>
</table>

## **CarouselBanner1**

主視覺banner輪播模組, 可透過點擊下方pagination切換下張輪播.  
****可依需求修改欄位：  
1. 加入輪播項目 \(可放置1-5個\)   
2. 大標: 最大字符串長度&lt;60 \(60個字元\), 大網建議最多2行  
3. 按鈕: 文字最大字符串長度&lt;20 \(20個字元\)  
4. 更換背景圖: 大網 1920\*470px 小網750\*900px \(小網實際顯示尺寸375\*450px\)

{% tabs %}
{% tab title="Web" %}
![](../.gitbook/assets/carouselbanner1-1920x470.jpg)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/carouselbanner1-750x900%20%281%29.jpg)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Usage" %}
```jsx
import CarouselBanner1 from '../components/partials/banner/CarouselBanner1';

<CarouselBanner1
  items={[
    {
      image: {
        md: '/resources/product/images/ebu-aws-banner.png',
        sm: '/resources/product/images/ebu-aws-banner-mb.jpg'
      },
      title: '導入遠傳AWS雲端託管，讓您不再投入大量資金與人力維護傳統機房。',
      action: {
        text: '免費諮詢',
        link: '#',
      },
    },
    {
      image: {
        md: '/resources/product/images/ebu-aws-banner.png',
        sm: '/resources/product/images/ebu-aws-banner-mb.jpg'
      },
      title: '導入遠傳AWS雲端託管，讓您不再投入大量資金與人力維護傳統機房。',
      action: {
        text: '免費諮詢',
        link: '#',
      },
    },
    {
      image: {
        md: '/resources/product/images/ebu-aws-banner.png',
        sm: '/resources/product/images/ebu-aws-banner-mb.jpg'
      },
      title: '導入遠傳AWS雲端託管，讓您不再投入大量資金與人力維護傳統機房。',
      action: {
        text: '免費諮詢',
        link: '#',
      },
    },
    {
      image: {
        md: '/resources/product/images/ebu-aws-banner.png',
        sm: '/resources/product/images/ebu-aws-banner-mb.jpg'
      },
      title: '導入遠傳AWS雲端託管，讓您不再投入大量資金與人力維護傳統機房。',
      action: {
        text: '免費諮詢',
        link: '#',
      },
    },
  ]}
/>
```
{% endtab %}

{% tab title="CarouselBanner1.js" %}
```jsx
import React from 'react';
import Slider from 'react-slick';
import Button from '../../Button';

import PropTypes from 'prop-types'

const CarouselBanner1 = props => {
  const [isMobile, setIsMobile] = React.useState(window.innerWidth < 768);

  React.useEffect(() => {
    window.addEventListener('resize', e => {
      setIsMobile(window.innerWidth < 768)
    })
  })

  const settings = {
    arrows: false,
    autoPlay: true,
    dots: true,
    infinite: true,
    draggable: true,
  }

  return (
    <section className="fui-banner is-product">
      <Slider {...settings}>
        {
          props.items.map((item, i) => (
            <div key={`carousel-banner-1-${i}`}>
              <div className="bg" style={{
                backgroundImage: `url(${isMobile ? item.image.sm : item.image.md})`
              }}>
              </div>
              <div className="fui-container">
                  <div className="caption">
                      <h1 className="mt-0 with-quote">
                          {item.title}
                      </h1>
                      <Button {...item.action} btnStyle='primary'>{item.action.text}</Button>
                  </div>
              </div>
            </div>
          ))
        }
      </Slider>
    </section>
  )
}

CarouselBanner1.propTypes = {
  items: PropTypes.arrayOf(
    PropTypes.shape({
      title: PropTypes.string,
      image: PropTypes.shape({
        md: PropTypes.string,
        sm: PropTypes.string,
      }),
      action: PropTypes.shape({
          link: PropTypes.string,
          text: PropTypes.string
      }),
    })
  )
}

export default CarouselBanner1;
```
{% endtab %}
{% endtabs %}

#### Properties

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x540D;&#x7A31;</th>
      <th style="text-align:left">&#x5C6C;&#x6027;</th>
      <th style="text-align:left">&#x5FC5;&#x586B;</th>
      <th style="text-align:left">&#x9078;&#x9805;</th>
      <th style="text-align:left">&#x8AAA;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">items</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>{</p>
        <p>title: string
          <br />image:{md: &apos;/resources/product/images/ebu-aws-banner.png&apos;, sm:
          &apos;/resources/product/images/ebu-aws-banner-mb.jpg&apos;}
          <br />action: object
          <br />link: string</p>
        <p>text: string</p>
        <p>}</p>
      </td>
      <td style="text-align:left"></td>
    </tr>
  </tbody>
</table>

## CarouselBanner2

主視覺banner輪播模組, 可透過點擊下方pagination切換下張輪播. 可依需求修改欄位:  
1. 加入輪播項目 \(可放置1-5個\)   
2. 大標: 最大字符串長度&lt;30 \(30個字元\), 大網建議最多1行  
3. 小標: 文字最大字符串長度&lt;60 \(60個字元\), 大網建議最多1行  
4. 按鈕: 文字最大字符串長度&lt;20 \(20個字元\)  
5. 更換背景圖 \(1920x470px\)

{% tabs %}
{% tab title="Web" %}
![](../.gitbook/assets/image%20%28219%29.png)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/image%20%28233%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Usage" %}
```jsx
<CarouselBanner2
  items={[
    {
      image: {
        md: '/resources/product/images/bg-aws-banner.png',
        sm: '/resources/product/images/bs-awd-banner-sm.png',
      },
      title: '遠傳AWS雲端服務',
      description: '遠傳與Amazon合作，提供企業公有雲服務',
      action: {
        text: '免費諮詢',
        link: '#',
      },
    },
    {
      image: {
        md: '/resources/product/images/bg-aws-banner.png',
        sm: '/resources/product/images/bs-awd-banner-sm.png',
      },
      title: '遠傳AWS雲端服務',
      description: '遠傳與Amazon合作，提供企業公有雲服務',
      action: {
        text: '免費諮詢',
        link: '#',
      },
    },
    {
      image: {
        md: '/resources/product/images/bg-aws-banner.png',
        sm: '/resources/product/images/bs-awd-banner-sm.png',
      },
      title: '遠傳AWS雲端服務',
      description: '遠傳與Amazon合作，提供企業公有雲服務',
      action: {
        text: '免費諮詢',
        link: '#',
      },
    },
  ]}
/>
```
{% endtab %}

{% tab title="CarouselBanner2.js" %}
```jsx
import React from 'react';
import Button from '../../Button'

import Slider from 'react-slick';

import PropTypes from 'prop-types'

class CarouselBanner2 extends React.Component {
  // console.log(color)
  render() {
    return (
      <section className="fui-banner is-product is-style-2">
        <Slider arrows={false} autoPlay={true} dots={true} infinite={true} draggable={true}>
          {
            this.props.items.map((item, i) => (
              <div key={`carousel-banner-2-${i}`}>
                <div className="banner-img">
                  <div className="d-none d-sm-block" style={{ backgroundImage: `url(${item.image.md})` }}></div>
                  <div className="d-block d-sm-none" style={{ backgroundImage: `url(${item.image.sm})` }}></div>
                </div>
                {/* <img src={item.image.md} srcSet={item.image.retinaMd || item.image.md} className='d-none d-sm-block' alt={item.title} />
                <img src={item.image.sm} srcSet={item.image.retinaSm || item.image.sm} className="d-block d-sm-none" alt={item.title} /> */}
                <div className="fui-container">
                  <div className="caption">
                    <h1 className="my-0" dangerouslySetInnerHTML={{ __html: item.title }}></h1>
                    <p className="subtitle mt-0">{item.description}</p>
                    <Button {...item.action} btnStyle='primary'>{item.action.text}</Button>
                  </div>
                </div>
              </div>
            ))
          }
        </Slider>
      </section>
    )
  }
}

CarouselBanner2.propTypes = {
  items: PropTypes.arrayOf(
    PropTypes.shape({
      title: PropTypes.string,
      description: PropTypes.string,
      image: PropTypes.shape({
        md: PropTypes.string,
        retinaMd: PropTypes.string,
        sm: PropTypes.string,
        retinaSm: PropTypes.string
      }),
      action: PropTypes.shape({
        icon: PropTypes.string,
        link: PropTypes.string,
        text: PropTypes.string
      }),
    })
  )
}

export default CarouselBanner2;
```
{% endtab %}
{% endtabs %}

#### Properties

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x540D;&#x7A31;</th>
      <th style="text-align:left">&#x5C6C;&#x6027;</th>
      <th style="text-align:left">&#x5FC5;&#x586B;</th>
      <th style="text-align:left">&#x9078;&#x9805;</th>
      <th style="text-align:left">&#x8AAA;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">items</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>{</p>
        <p>title: string
          <br />image: object
          <br />md: string
          <br />sm: string
          <br />action: object
          <br />link: string</p>
        <p>text: string</p>
        <p>}</p>
      </td>
      <td style="text-align:left"></td>
    </tr>
  </tbody>
</table>

### 

## CarouselBanner3

主視覺banner輪播模組, 可使用在廣告類banner, 可透過點擊下方pagination切換下張輪播, 可依需求修改欄位:  
1. 加入輪播項目 \(可放置1-5個\)   
2. 小標: 文字最大字符串長度&lt;60 \(60個字元\), 大網建議最多1行   
3. 大標: 最大字符串長度&lt;30 \(30個字元\), 大網建議最多1行  
4. 按鈕: 文字最大字符串長度&lt;20 \(20個字元\)  
5. 更換背景圖 \(1920x470px\)

{% tabs %}
{% tab title="Web" %}
![](../.gitbook/assets/image%20%2848%29.png)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/image%20%28141%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Usage" %}
```jsx
import CarouselBanner3 from '../components/partials/carousel/CarouselBanner3';

export const sliders = [
  {
    id: '001',
    type: '頭家輕鬆配系列產品',
    title: '市內電話輕鬆省',
    img: '/resources/ebu/images/ebu-telephone-banner-1440x460.jpg',
    link: '#',
  },
  {
    id: '002',
    type: '頭家輕鬆配系列產品',
    title: '市內電話輕鬆省',
    img: '/resources/ebu/images/ebu-solution.jpg',
    link: '#',
  },
  {
    id: '003',
    type: '頭家輕鬆配系列產品',
    title: '市內電話輕鬆省',
    img: '/resources/ebu/images/ebu-solution.jpg',
    link: '#',
  },
  {
    id: '004',
    type: '頭家輕鬆配系列產品',
    title: '市內電話輕鬆省',
    img: '/resources/ebu/images/ebu-solution.jpg',
    link: '#',
  },
];

<CarouselBanner3 slider={Mock.sliders} />
```
{% endtab %}

{% tab title="CarouselBanner3.js" %}
```jsx
import React from 'react';
import Slider from "react-slick";
import Button from '../../Button'
import PropTypes from 'prop-types';
class CarouselBanner3 extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      isMobile: window.innerWidth < 960,
    }
  }

  render() {
    const settings = {
      dots: true,
      accessibility: false,
      adaptiveHeight: false,
      infinite: true,
      slidesToShow: 1,
      slidesToScroll: 1,
      autoplay: false,
      speed: 500,
      arrows: false,
      autoplaySpeed: 5000,
      cssEase: "linear",
      customPaging: i => <button key={i}></button>
    };

    return (
      <div className="carousel-banner-3">
        <Slider {...settings}>
          {this.props.slider.map(slide => {
            return (
              <div key={slide.title} className="slide">
                <div className="bg-img" style={{ backgroundImage: `url(${slide.img})` }}></div>
                {/* <img className="bg-img" src={slide.img} alt="bg-img" /> */}
                <div className="fui-container">
                  <div className="content-wrapper">
                    <div className="content">
                      <p className="subtitle is-text-white">{slide.type}</p>
                      <h1 className="is-text-white">{slide.title}</h1>
                      <Button link={slide.link} btnStyle='secondary' className="is-large is-reverse">看更多</Button>
                    </div>
                  </div>
                </div>
              </div>
            )
          })}
        </Slider>
      </div>
    )
  }
}

CarouselBanner3.propTypes = {
  slider: PropTypes.arrayOf(
    PropTypes.shape({
      img: PropTypes.string.isRequired,
      type: PropTypes.string.isRequired,
      title: PropTypes.string.isRequired,
      link: PropTypes.string
    })
  )
}

export default CarouselBanner3
```
{% endtab %}
{% endtabs %}

#### Properties

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x540D;&#x7A31;</th>
      <th style="text-align:left">&#x5C6C;&#x6027;</th>
      <th style="text-align:left">&#x5FC5;&#x586B;</th>
      <th style="text-align:left">&#x9078;&#x9805;</th>
      <th style="text-align:left">&#x8AAA;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">slider</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>{</p>
        <p>img: string
          <br />type: string
          <br />title: string
          <br />link: string</p>
        <p>}</p>
      </td>
      <td style="text-align:left"></td>
    </tr>
  </tbody>
</table>

## CarouselBanner4

輪播型主視覺牌卡模組, 小網隱藏內文, 可依需求修改欄位:  
1. 小標: 文字最大字符串長度&lt;20 \(20個字元\), 大網建議最多1行   
2. 大標: 最大字符串長度&lt;30 \(30個字元\), 大網建議最多2行  
3. 內文: 文字最大字符串長度&lt;100 \(100個字元\), 大網建議最多1行  
4. 按鈕: 文字最大字符串長度&lt;20 \(20個字元\)  
5. 更換長寬比1:1靜態圖 \(1600x1600px or 800x800px\)

{% tabs %}
{% tab title="Web" %}
![](../.gitbook/assets/image%20%2861%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Usage" %}
```jsx
import CarouselBanner4 from '../components/partials/carousel/CarouselBanner4';

export const slider = [
  {
    videoId: '9FaXQK51iM8',
    articleType: '數位轉型案例',
    title: '遠傳數位轉型最佳夥伴-台灣大車隊現身說法',
    content: '遠傳持續深耕各產業前數位科技領域，已為上千家企業完成數位轉型，並啟動國內第一個NB-IoT物聯。',
    img: '/resources/ebu/images/taiwan-taxi-red-woman-300x300.jpg',
    videoLink: "",
    alterVideo: 'http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/ElephantsDream.mp4',
    socialLink: {
      line: "",
      fb: ""
    }
  },
  {
    videoId: '9FaXQK51iM8',
    alterVideo: 'http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/ElephantsDream.mp4',
    articleType: '數位轉型案例',
    title: '數位轉型案例1',
    content: '連鎖餐飲龍頭集團執行「去機房、上雲端」的計畫，利用遠傳雲端，把硬體與核心ERP/POS轉移到私有雲。',
    link: '#',
    videoLink: 'https://youtu.be/9FaXQK51iM8',
    img: '/resources/ebu/images/taiwan-taxi-red-woman-300x300.jpg',
    socialLink: {
      line: "",
      fb: ""
    }
  },
  {
    videoId: null,
    alterVideo: '',
    articleType: '數位轉型案例',
    title: '數位轉型案例1',
    content: '連鎖餐飲龍頭集團執行「去機房、上雲端」的計畫，利用遠傳雲端，把硬體與核心ERP/POS轉移到私有雲。',
    link: '#',
    img: '/resources/ebu/images/taiwan-taxi-red-woman-300x300.jpg',
    socialLink: {
      line: "",
      fb: ""
    }
  },
  {
    videoId: null,
    alterVideo: '',
    articleType: '數位轉型案例',
    title: '數位轉型案例1',
    content: '連鎖餐飲龍頭集團執行「去機房、上雲端」的計畫，利用遠傳雲端，把硬體與核心ERP/POS轉移到私有雲。',
    link: '#',
    img: '/resources/ebu/images/taiwan-taxi-red-woman-300x300.jpg',
    socialLink: {
      line: "",
      fb: ""
    }
  },
];

<CarouselBanner4 slider={PerformanceMock.slider} />
```
{% endtab %}

{% tab title="CarouselBanner4.js" %}
```jsx
import React from 'react';
import Slider from 'react-slick';
import VideoModal from '../../VideoModel';
import { Link } from 'react-router-dom';
import PropTypes from 'prop-types';
class CarouselBanner4 extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      isMobile: window.innerWidth < 960,
      currentVideo: null,
      openModal: false,
    };

    this.playVideo = this.playVideo.bind(this);
  }
  closeModal = () => {
    this.setState({
      openModal: false,
      currentVideo: '',
      alterVideo: '',
    });
  };

  playVideo(slide) {
    this.setState({
      openModal: true,
      currentVideo: slide.videoLink,
      alterVideo: slide.alterVideo,
    });
  }

  render() {
    const settings = {
      dots: true,
      accessibility: false,
      adaptiveHeight: false,
      infinite: true,
      slidesToShow: 1,
      slidesToScroll: 1,
      autoplay: false,
      speed: 500,
      arrows: false,
      autoplaySpeed: 5000,
      cssEase: 'linear',
      customPaging: i => <button key={i}></button>,
    };

    return (
      <div className='carousel-banner-4'>
        <VideoModal open={this.state.openModal} videoUrl={this.state.currentVideo} alterVideo={this.state.alterVideo} onClose={this.closeModal} />
        <Slider {...settings}>
          {this.props.slider.map(slide => {
            return (
              <div key={slide.title} className='slide'>
                <div className='fui-container'>
                  <div className='content-wrapper'>
                    {/* <div className="mb-img"> */}
                    <div className='position-relative'>
                      <img
                        onClick={!!slide.videoId ? () => this.playVideo(slide) : null}
                        className='mb-img-reveal'
                        src={slide.img}
                        alt='reveal'
                      />
                      {!!slide.videoId ? (
                        <div className='play'>
                          <div className='round'></div>
                        </div>
                      ) : (
                          ''
                        )}
                    </div>
                    <div className='fui-card content'>
                      <div className='main-img'>
                        <img
                          onClick={!!slide.videoId ? () => this.playVideo(slide) : null}
                          className=''
                          src={slide.img}
                          alt='reveal'
                        />
                      </div>
                      <div className='content-info'>
                        <h5 className='head'>{slide.articleType}</h5>
                        <h1>{slide.title}</h1>
                        <h5 className='content-text'>{slide.content}</h5>
                        <div className='bottom'>
                          {!!slide.videoId ? (
                            <button
                              onClick={() => this.playVideo(slide)}
                              className={`fui-button m-0 ${this.state.isMobile ? 'is-arrow' : 'is-primary'}`}>
                              <span className=''>看影片</span>
                            </button>
                          ) : (
                              <Link
                                to={slide.link}
                                className={`fui-button m-0 ${this.state.isMobile ? 'is-arrow' : 'is-primary'}`}>
                                <span>看更多</span>
                              </Link>
                            )}
                          <div className='social'>
                            <Link to={slide.socialLink.fb}>
                              <i className={`icon-facebook-sm`}></i>
                            </Link>
                            <Link to={slide.socialLink.line}>
                              <i className={`icon-line-sm`}></i>
                            </Link>
                          </div>
                        </div>
                      </div>
                    </div>
                    <div className='left-triangle' />
                    <div className='right-triangle' />
                  </div>
                </div>
                <div className="background" style={{ backgroundImage: `url(/resources/ebu/images/video-new-620@2x.png)` }}></div>
                <div className="background-mb" style={{ backgroundImage: `url(/resources/ebu/images/video-new-620@2x.png)` }}></div>
                {/* <img className='background-mb' src='/resources/ebu/images/video-new@2x.png' alt="background-mb" />
                <img className='background' src='/resources/ebu/images/video-new-620@2x.png' alt="background" /> */}
                {/* <img className="img-reveal" src={slide.img} alt="reveal" /> */}
              </div>
            );
          })}
        </Slider>
      </div>
    );
  }
}

CarouselBanner4.propTypes = {
  slider: PropTypes.arrayOf(
    PropTypes.shape({
      videoId: PropTypes.string, // videoId
      img: PropTypes.string.isRequired,
      articleType: PropTypes.string.isRequired,
      title: PropTypes.string.isRequired,
      content: PropTypes.string.isRequired,
      link: PropTypes.string, // link
      videoLink: PropTypes.string, // videoId or link
      alterVideo: PropTypes.string, // video link
      socialLink: PropTypes.shape({
        fb: PropTypes.string, // facebook link
        line: PropTypes.string  // line link
      }),
    })
  ),
};

export default CarouselBanner4;

```
{% endtab %}
{% endtabs %}

#### Properties

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x540D;&#x7A31;</th>
      <th style="text-align:left">&#x5C6C;&#x6027;</th>
      <th style="text-align:left">&#x5FC5;&#x586B;</th>
      <th style="text-align:left">&#x9078;&#x9805;</th>
      <th style="text-align:left">&#x8AAA;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">slider</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>{</p>
        <p>videoId: string
          <br />alterVideo: string
          <br />articleType: string.required
          <br />title: string.required
          <br />content: string.required
          <br />link: string
          <br />img: string.required
          <br />socailLink: object
          <br />line: string
          <br />fb: string</p>
        <p>}</p>
      </td>
      <td style="text-align:left"><b>link</b> &#x8207; <b>videoId</b> &#x4E8C;&#x64C7;&#x4E00;&#x8F38;&#x5165;</td>
    </tr>
  </tbody>
</table>

## DemoShop

{% tabs %}
{% tab title="Desktop" %}
![](../.gitbook/assets/image%20%28106%29.png)
{% endtab %}

{% tab title="Mobile" %}


![](../.gitbook/assets/image%20%2837%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="First Tab" %}
```javascript
import DemoShop from '../components/partials/carousel/DemoShop';

<DemoShop
  id='example'
  marquee={false}
  title='聽頭家說'
  moreLink={{
    type: 'video',
    src: 'https://youtu.be/9FaXQK51iM8',
    alterVideo: '',
    text: '觀看影片實例',
  }}
  list={[
    {
      logo: '/resources/ebu/images/ebu-testimonial-logo/testimonial-logo-micro-01-4x3.png',
      logoWhite: '/resources/ebu/images/ebu-testimonial-logo/testimonial-logo-micro-01-white-4x3.png',
      name: 'The 41 Bistro - 肆拾壹號英式小酒館',
      meta: '',
      content:
        'Smart Wifi 的功能很多樣且彈性，可以自由選擇、設定。對於沒有多餘行銷人力的小店家來說很方便，取代以往自己設計活動耗費的時間。',
    },
    {
      logo: '/resources/ebu/images/ebu-testimonial-logo/testimonial-logo-micro-02-4x3.png',
      logoWhite: '/resources/ebu/images/ebu-testimonial-logo/testimonial-logo-micro-02-white-4x3.png',
      name: '花草慢時光',
      meta: '',
      content:
        'Smart Wifi 的功能很多樣且彈性，可以自由選擇、設定。對於沒有多餘行銷人力的小店家來說很方便，取代以往自己設計活動耗費的時間。',
    },
    {
      logo: '/resources/ebu/images/ebu-testimonial-logo/testimonial-logo-micro-03-4x3.png',
      logoWhite: '/resources/ebu/images/ebu-testimonial-logo/testimonial-logo-micro-03-white-4x3.png',
      name: 'Korea salon',
      meta: '',
      content:
        'Smart Wifi 的功能很多樣且彈性，可以自由選擇、設定。對於沒有多餘行銷人力的小店家來說很方便，取代以往自己設計活動耗費的時間。',
    },
    {
      logo: '/resources/ebu/images/ebu-testimonial-logo/testimonial-logo-micro-04-4x3.png',
      logoWhite: '/resources/ebu/images/ebu-testimonial-logo/testimonial-logo-micro-04-white-4x3.png',
      name: '楓露',
      meta: '',
      content:
        'Smart Wifi 的功能很多樣且彈性，可以自由選擇、設定。對於沒有多餘行銷人力的小店家來說很方便，取代以往自己設計活動耗費的時間。',
    },
  ]}
/>
```
{% endtab %}

{% tab title="Source code" %}
```javascript
import React from 'react';
import { Grid } from '@material-ui/core';
import { Link } from 'react-router-dom';
import Slider from 'react-slick';
import Marquee from '../../Marquee';
import PropTypes from 'prop-types';
import VideoModal from '../../VideoModel';

import ArrowLeftWhite from '../../animateArrow/ArrowLeftWhite';

const DemoShop = props => {
  const settings = {
    infinite: true,
    speed: 1000,
    autoplaySpeed: 7000,
    slidesToShow: 1,
    slidesToScroll: 1,
    pauseOnHover: true,
  };
  const [modalOpen, setModalOpen] = React.useState(false);
  const [currentVideo, setCurrentVideo] = React.useState('');
  const [alterVideo, setAlterVideo] = React.useState('');
  // let modalOpen = false;
  // let currentVideo = '';
  // let alterVideo = '';
  const marqueeData = props.list.reduce((accumulator, value, index, array) => {
    accumulator.push({ img: value.logo });
    return accumulator;
  }, []);

  const prevSlider = React.useRef(null);
  const nextSlider = React.useRef(null);

  const updateSlider = (oldIndex, newIndex) => {
    if (window.innerWidth < 768) return;

    prevSlider.current.slickGoTo(newIndex);
    nextSlider.current.slickGoTo(newIndex);
  };

  const setPrevSlide = () => {
    let prevData = [...props.list];
    let last = prevData.pop();
    prevData = [last].concat(prevData);
    return prevData;
  };

  const setNextSlide = () => {
    let nextData = [...props.list];
    let first = nextData.shift();
    nextData.push(first);
    return nextData;
  };

  const prevData = setPrevSlide();
  const nextData = setNextSlide();


  const openVideoModal = data => {
    setModalOpen(true);
    if (!!props.moreLink.src) {
      setCurrentVideo(props.moreLink.src);
      setAlterVideo('')
    } else {
      setCurrentVideo('');
      setAlterVideo(props.moreLink.alterVideo)
    }
  };
  const closeModal = () => {
    setModalOpen(false);
    setCurrentVideo('');
    setAlterVideo('')
  };
  return (
    <section className='demo-shop' id={props.id}>
      <VideoModal open={modalOpen} videoUrl={currentVideo} alterVideo={alterVideo} onClose={() => closeModal()} />
      <ArrowLeftWhite />
      <div className='fui-container'>
        <div className='fui-section-header'>
          <h2 className='section-title'>{props.title}</h2>
          {typeof props.moreLink === 'string' ? (
            <Link to={props.moreLink} className='fui-button is-text'>
              <span>看更多</span>
              <i className='icon-chevron-right'></i>
            </Link>
          ) : (
              <button onClick={() => { openVideoModal() }} datasrc={props.moreLink.src} className='fui-button is-text'>
                <span>{props.moreLink.text}</span>
                <i className='icon-chevron-right'></i>
              </button>
            )}
        </div>

        <Grid container>
          <Grid item md={3} className='carousen-container'>
            
            <Slider className='shop-carousel is-prev' ref={prevSlider} {...settings} arrows={false}>
              {prevData.map((item, idx) => (
                <div key={`carousel-${idx}`} align='center' className='shop-carousel-item'>
                  {item.logo ? <img src={item.logo} alt={item.name} height='140' /> : ''}
                  <p>{item.name} </p>
                </div>
              ))}
            </Slider>
          </Grid>
          <Grid item xs={12} sm={12} md={6} className='carousen-container'>
            
            <Slider
              className='shop-carousel is-main'
              dots={true}
              arrows={true}
              autoplay={true}
              beforeChange={updateSlider}
              {...settings}>
              {props.list.map((item, idx) => (
                <Link key={`carousel-${idx}`} to={item.link} className='shop-carousel-item'>
                  <div>
                    {item.logoWhite ? (
                      <img src={item.logoWhite} srcSet={item.retinaLogoWhite} alt={item.name} className='logo' />
                    ) : (
                        ''
                      )}

                    <h6>{item.content}</h6>
                    <div className='shop-name'>
                      {item.name}
                      <br />
                      {item.meta !== '' ? item.meta : ''}
                    </div>
                  </div>
                </Link>
              ))}
            </Slider>
          </Grid>
          <Grid item md={3} className='carousen-container'>
            
            <Slider className='shop-carousel is-next' ref={nextSlider} {...settings} arrows={false}>
              {nextData.map((item, idx) => (
                <div key={`carousel-${idx}`} align='center' className='shop-carousel-item'>
                  {item.logo ? (
                    <img src={item.logo} srcSet={item.retinaLogo || item.logo} alt={item.name} height='140' />
                  ) : (
                      ''
                    )}
                  <p>{item.name} </p>
                </div>
              ))}
            </Slider>
          </Grid>
        </Grid>
        {props.marquee === 'undefined' || props.marquee === true ? (
          <Marquee direction={'landscape'} loopData={marqueeData} />
        ) : (
            ''
          )}
      </div>
    </section>
  );
};

DemoShop.propTypes = {
  marquee: PropTypes.bool,
  title: PropTypes.string,
  moreLink: PropTypes.oneOfType([
    PropTypes.string,
    PropTypes.shape({
      type: PropTypes.string,
      src: PropTypes.string,
      alterVideo: PropTypes.string,
      text: PropTypes.string,
    })
  ]),
  list: PropTypes.arrayOf(
    PropTypes.shape({
      logoWhite: PropTypes.string,
      retinaLogoWhite: PropTypes.string,
      logo: PropTypes.string,
      retinaLogo: PropTypes.string,
      background: PropTypes.string,
      meta: PropTypes.string,
      name: PropTypes.string,
      content: PropTypes.string,
      link: PropTypes.string,
    })
  ),
};

export default DemoShop;

```
{% endtab %}
{% endtabs %}

#### Properties

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x540D;&#x7A31;</th>
      <th style="text-align:left">&#x5C6C;&#x6027;</th>
      <th style="text-align:left">&#x5FC5;&#x586B;</th>
      <th style="text-align:left">&#x9078;&#x9805;</th>
      <th style="text-align:left">&#x8AAA;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">marquee</td>
      <td style="text-align:left">bool</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x662F;&#x5426;&#x8F2A;&#x64AD;</td>
    </tr>
    <tr>
      <td style="text-align:left">title</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x6A19;&#x984C;</td>
    </tr>
    <tr>
      <td style="text-align:left">moreLink</td>
      <td style="text-align:left">
        <p>string</p>
        <p>or</p>
        <p>object</p>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left">{
        <br />type: string,
        <br />src: string,
        <br />alterVideo: string,
        <br />text: string
        <br />}</td>
      <td style="text-align:left">
        <p>&#x5982;&#x679C;&#x53C3;&#x6578;&#x70BA;&#x5B57;&#x4E32;&#xFF0C;&#x5247;&#x5C0E;&#x5165;&#x9023;&#x7D50;</p>
        <p>&#x5426;&#x5247;&#x9700;&#x5E36;&#x5165;&#x7269;&#x4EF6;&#xFF0C;&#x57F7;&#x884C;&#x5F71;&#x7247;&#x64AD;&#x653E;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">list</td>
      <td style="text-align:left">array</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">[{
        <br />logoWhite: string,
        <br />retinaLogoWhite: string,
        <br />logo: string,
        <br />retinaLogo: string,
        <br />background: string,
        <br />meta: string,
        <br />name: string,
        <br />content: string,
        <br />link: string
        <br />}]</td>
      <td style="text-align:left">
        <p>retinaLogo &#x82E5;&#x6C92;&#x8F38;&#x5165;&#xFF0C;&#x5247;&#x9810;&#x8A2D;&#x70BA;&#x4E00;&#x822C;
          logo</p>
        <p>nam &#x6A19;&#x984C;
          <br />meta &#x526F;&#x6A19;&#x984C;</p>
        <p>content &#x63CF;&#x8FF0;</p>
      </td>
    </tr>
  </tbody>
</table>

## SectionCarousel1

{% tabs %}
{% tab title="Desktop" %}
![](../.gitbook/assets/image%20%28159%29.png)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/image%20%28138%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Usage" %}
```javascript
import SectionCarousel1 from '../components/partials/card/SectionCarousel1';

<SectionCarousel1 {...EbuLarge.promotionCard} />

export const promotionCard = {
  title: '您可能有興趣',
  cards: [
    {
      image: '/resources/ebu/images/ebu-medium-banner-01.jpg',
      meta: '企業通訊與系統整合',
      title: '企業上雲超靈活',
      description: '多元的雲端服務，從私有雲、公有雲到混合雲，讓企業輕鬆享有高端的服務...',
      link: '#',
    },
    {
      image: '/resources/ebu/images/ebu-medium-banner-02.jpg',
      meta: '企業資安',
      title: '企業資安再進化',
      description: '多年的資安專業技術，提供企業高效益的資安防護計畫。',
      link: '#',
    },
    {
      image: '/resources/ebu/images/ebu-medium-banner-03.jpg',
      meta: '雲端服務',
      title: '萬物聯網現商機',
      description: '迎接多重裝置連結的萬物互聯時代，透過需求勾勒物聯網未來樣貌，為產業',
      link: '#',
    },
  ],
  more: { text: '大型企業全系列產品', link: '#product-map' },
};

```
{% endtab %}

{% tab title="SectionCarousel1.js" %}
```javascript
import React from 'react';
import Slider from "react-slick";
import {NavLink} from 'react-router-dom';

import ArrowLeftWhite from '../../animateArrow/ArrowLeftWhite';
import ArrowRightWhite from '../../animateArrow/ArrowRightWhite';
import ProductBgArrow from '../../animateArrow/ProductBgArrow';
import Card from '../../card/Card';

import PropTypes from 'prop-types';

const SectionCarousel1 = (props) => {
    const setting = {
        dots: false,
        infinite: false,
        slidesToShow: 3,
        draggable: true,
        responsive: [
            {
                breakpoint: 960,
                settings: {
                    arrows: true,
                    slidesToShow: 3,
                    slidesToScroll: 3,
                    infinite: true,
                    dots: false
                }
            },
            {
                breakpoint: 768,
                settings: {
                    arrows: true,
                    slidesToShow: 2,
                    variableWidth: true
                }
            },
            {
                breakpoint: 480,
                settings: {
                    arrows: true,
                    slidesToShow: 1,
                    variableWidth: true
                }
            }
        ]
    }

    const renderBg = () => {
        switch(props.bgStyle) {
            case 'arrow': 
                return <div className="section-bg"><ProductBgArrow/></div>
            default: 
                return (
                    <div className="section-bg">
                        <ArrowLeftWhite/>
                        <ArrowRightWhite/>
                    </div>
                )
        }
    }
    return (
        <section className="fui-horzonal-cards" id={props.id}>
            {renderBg()}
            <div className="fui-container">
                <h2 className="section-title">
                    {props.title}
                </h2>
                <Slider {...setting} className="horizontal-cards">
                    {
                        props.cards.map((card, idx) => (
                            <Card key={idx} {...card} style={{width: 270}} />
                        ))
                    }
                </Slider>
                {
                    props.more ? (
                        <div className="align-center">
                            <NavLink to={props.more.link} className="fui-more">
                                {props.more.text}<br/>
                                <i className='icon-chevron-down'></i>
                            </NavLink>
                        </div>
                    ) : ''
                }
            </div>
        </section>
    );
}

SectionCarousel1.propTypes = {
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

export default SectionCarousel1;
```
{% endtab %}
{% endtabs %}

#### Properties

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x540D;&#x7A31;</th>
      <th style="text-align:left">&#x5C6C;&#x6027;</th>
      <th style="text-align:left">&#x5FC5;&#x586B;</th>
      <th style="text-align:left">&#x9078;&#x9805;</th>
      <th style="text-align:left">&#x8AAA;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">title</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">cards</td>
      <td style="text-align:left">array</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x6B04;&#x4F4D;&#x53EF;&#x53C3;&#x8003; <a href="https://app.gitbook.com/@ajacreative/s/fetnet-1/~/drafts/-M1UwW6hQrq6o_OTbp_Z/components/card">Card</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">more</td>
      <td style="text-align:left">object</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>{</p>
        <p>text: string,
          <br />link: string</p>
        <p>}</p>
      </td>
      <td style="text-align:left"></td>
    </tr>
  </tbody>
</table>

## VideoCarousel

![](../.gitbook/assets/image%20%28244%29.png)

{% tabs %}
{% tab title="React JSX" %}
```jsx
import VideoCarousel from '../components/VideoCarousel';

<VideoCarousel
          title="一探5G世界"
          videos={[
            {
              videoId: '9FaXQK51iM8',
              title: '遠傳x17 Media',
              content: '全台首發用5G訊號直播實境節目',
              imgSmall: '/resources/cbu/img/video-02.jpg',
              imgLarge: '/resources/cbu/img/video-02.jpg',
              videoLink: 'df-gMDkuC08',
              alterVideo: null,
            },
            {
              videoId: '9FaXQK51iM8',
              title: '2019台北跨年晚會',
              content: '幕後紀實影片',
              imgSmall: '/resources/cbu/img/video-03.jpg',
              imgLarge: '/resources/cbu/img/video-03.jpg',
              videoLink: 'https://youtu.be/u9YYwJKQ0aQ',
              alterVideo: null,
            },
            {
              videoId: '9FaXQK51iM8',
              title: '遠傳AI智慧驗布機',
              content: '',
              imgSmall: '/resources/cbu/img/video-01.jpg',
              imgLarge: '/resources/cbu/img/video-01.jpg',
              videoLink: 'https://youtu.be/CwfE29SgSZE',
              alterVideo: 'http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/ElephantsDream.mp4',
            }
          ]}
        />
```
{% endtab %}

{% tab title="" %}
```jsx
import React, { Component } from 'react';
import VideoModal from './VideoModal'
import Slider from 'react-slick';
import PropTypes from 'prop-types';
class VideoCarousel extends Component {
  constructor(props) {
    super(props);
    this.VideoSlideSetting = {
      dots: false,
      infinite: false,
      arrows: true,
      slidesToShow: 1,
      draggable: true,
    };
    this.state = {
      currentVideo: '',
      modalOpen: false
    }
  }
  openVideoModal = data => {
    this.setState({
      modalOpen: true,
      alterVideo: null,
      currentVideo: this.state.video,
    });
  };

  closeModal = () => {
    this.setState({
      modalOpen: false,
      alterVideo: '',
      currentVideo: '',
    });
  };
  render() {
    return (
      <section className='fui-horzonal-cards video-carousel is-narrow' id='video-slider'>
        <div className='fui-container'>
          <h2 className='section-title m-0 p-0'>{this.props.title}</h2>
          <Slider {...this.VideoSlideSetting} className='horizontal-cards mb-0'>
            {this.props.videos.map((card, idx) => (
              <div key={idx} className='video-card' onClick={() => this.openVideoModal(card)}>
                <div className='video-card-text'>
                  <div className='subtitle'>{card.title}</div>
                  <small>{card.content}</small>
                </div>
                <div className="video-img" style={{ backgroundImage: `url(${card.imgLarge})` }}></div>
                <div className="mask"></div>
              </div>
            ))}
          </Slider>
        </div>
        <VideoModal
          open={this.state.modalOpen}
          alterVideo={this.state.alterVideo}
          videoUrl={this.state.currentVideo}
          onClose={this.closeModal}
        />
      </section>
    );
  }
}

VideoCarousel.propTypes = {
  title: PropTypes.string,
  videos: PropTypes.arrayOf(
    PropTypes.shape({
      videoId: PropTypes.string,
      title: PropTypes.string,
      content: PropTypes.string,
      imgSmall: PropTypes.string,
      imgLarge: PropTypes.string,
      videoLink: PropTypes.string,
      alterVideo: PropTypes.string
    })
  ).isRequired
}
export default VideoCarousel;
```
{% endtab %}
{% endtabs %}



#### Properties

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x540D;&#x7A31;</th>
      <th style="text-align:left">&#x5C6C;&#x6027;</th>
      <th style="text-align:left">&#x5FC5;&#x586B;</th>
      <th style="text-align:left">&#x9078;&#x9805;</th>
      <th style="text-align:left">&#x8AAA;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">title</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">false</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">videos</td>
      <td style="text-align:left">array</td>
      <td style="text-align:left">true</td>
      <td style="text-align:left">
        <p>array&#x88E1;&#x7684;&#x7D50;&#x69CB;&#xFF1A;</p>
        <p>videoId: &apos;9FaXQK51iM8&apos;,
          <br />title: &apos;&#x9060;&#x50B3;AI&#x667A;&#x6167;&#x9A57;&#x5E03;&#x6A5F;&apos;,
          <br
          />content: &apos;&apos;, imgSmall: &apos;/resources/cbu/img/video-01.jpg&apos;,
          <br
          />imgLarge: &apos;/resources/cbu/img/video-01.jpg&apos;,
          <br />videoLink: &apos;<a href="https://youtu.be/CwfE29SgSZE">https://youtu.be/CwfE29SgSZE</a>&apos;,
          <br
          />alterVideo: &apos;<a href="http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/ElephantsDream.mp4">http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/ElephantsDream.mp4</a>&apos;,</p>
      </td>
      <td style="text-align:left">&#x53EA;&#x6709;&#x55AE;&#x4E00;&#x7B46;&#x8CC7;&#x6599;&#xFF0C;&#x5C31;&#x4E0D;&#x6703;&#x51FA;&#x73FE;&#x7BAD;&#x982D;&#x8207;carousel</td>
    </tr>
  </tbody>
</table>

## 社群行銷牌卡 CardPost -&gt; 直接沿用SectionCarousel1

![](../.gitbook/assets/image%20%28200%29.png)

{% tabs %}
{% tab title="React JSX" %}
```jsx
import SectionCarousel1 from '../../components/partials/card/SectionCarousel1';

<SectionCarousel1 {...{
  className: 'instagram mt-3 mt-md-0',
  title: '#遠傳樂享1加1',
  socialMedia: {
    line: {
      link: "#",
      target: "_blank"
    },
    facebook: {
      link: "#",
      target: "_blank"
    },
    title: "分享遠傳優惠"
  },
  cards: [
    {
      image: '/resources/cbu/img/cbu-promotion-post-1@2x.jpg',
      title: 'syuyikai',
      description: '挑戰✨遠傳iPhone11 樂享1+1 ✨ Kobe曾經在場上相Jordan討教投籃竅，...',
      link: "#",
    },
    {
      image: '/resources/cbu/img/cbu-promotion-post-2@2x.jpg',
      title: 'yylo11',
      description: '❤️遠傳iPhone11 樂享1+1❤️ 搶到跟自己打架的優惠在這兒💨',
      link: '#',
    },
    {
      image: '/resources/cbu/img/cbu-promotion-post-3@2x.jpg',
      title: 'uj85_',
      description: '遠傳iPhone11 樂享1+1 跟大家分享遠傳的優惠購機方案 🔥🔥',
      link: '#',
    },
    {
      image: '/resources/cbu/img/cbu-promotion-post-3@2x.jpg',
      title: 'ponponboxbox!',
      description: '遠傳iPhone11 樂享1+1 有人跟我一樣被iPhone11燒到嗎⁉️ 升級…',
      link: '#',
    },
  ]
}} />
```
{% endtab %}
{% endtabs %}

## CardFeature

![](../.gitbook/assets/image%20%2878%29.png)

{% tabs %}
{% tab title="Plain Text" %}
```jsx
import CardFeature from '../../components/partials/card/CardFeature';

<CardFeature
          titleColor="white"
          bgImg="/resources/cbu/img/cbu-goshare-bg-blue-1.svg"
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
{% endtab %}

{% tab title="" %}
```jsx
import React from 'react';
import Button from '../../Button';
import Item from '../../item/Item';
import Tooltip from '../../Tooltip';
import Slider from 'react-slick';
import PromotionCard from '../../card/PromotionCard';

import PropTypes from 'prop-types';

class CardFeature extends React.Component {
  constructor(props) {
    super(props);

    this.setting = {
      dots: false,
      infinite: false,
      slidesToShow: 3,
      draggable: true,
      responsive: [
        {
          breakpoint: 960,
          settings: {
            arrows: true,
            slidesToShow: 3,
            slidesToScroll: 3,
            infinite: true,
            dots: false,
          },
        },
        {
          breakpoint: 768,
          settings: {
            arrows: true,
            slidesToShow: 2,
            variableWidth: true,
          },
        },
        {
          breakpoint: 480,
          settings: {
            arrows: true,
            slidesToShow: 1,
            variableWidth: true,
          },
        },
      ],
    };
  }

  render() {
    return (
      <section className="plan-card" style={!!this.props.bgImg ? { backgroundImage: `url(${this.props.bgImg})`, backgroundSize: 'cover', backgroundPosition: 'bottom' } : null}>
        <div className="fui-container">
          <h2 style={this.props.titleColor ? { color: this.props.titleColor } : null}>{this.props.title}</h2>
          <Slider {...this.setting} className={`horizontal-cards is-rate-plan ${this.props.titleColor ? 'is-white-arrow' : ''}`}>
            {this.props.cards.map((card, idx) => {
              switch (card.type) {
                case 'promotion':
                  return (
                    <PromotionCard {...card} key={`plan-card-${idx}`} />
                  )
                case 'card01':
                  return (
                    <div className='fui-card is-bg-white' key={`plan-card-${idx}`}>
                      <div className="align-left">
                        {
                          card.image ? (<div className="fui-card-image">
                            <img src={card.image} alt="img" />
                          </div>) : null
                        }
                        <div className="fui-card-caption pt-4">
                          <div className="fui-card-content">
                            <h3 className="mb-3">{card.title}</h3>
                            {
                              card.description ? (
                                <div className="fui-card-description" dangerouslySetInnerHTML={{ __html: card.description }}></div>
                              ) : null
                            }
                            {
                              card.list ? (
                                <div className="fui-list">{
                                  card.list.map((item, i) => (
                                    <div className='item-with-tooltip' key={`plan-card-${idx}-item-${i}`}>
                                      <Item prefix='check'>
                                        {item.text}
                                      </Item>
                                    </div>
                                  ))
                                }</div>

                              ) : null
                            }
                          </div>
                        </div>
                      </div>
                    </div>
                  )
                  break;
                default:
                  return (
                    <div className='fui-card' key={`plan-card-${idx}`}>
                      <div className="fui-card-action align-center">
                        <div className="fui-card-caption">
                          {
                            card.image ? (<img src={card.image} alt="img" />) : null
                          }
                          {
                            card.ribbon ? (
                              <div className="fui-card-ribbon">{card.ribbon}</div>
                            ) : null
                          }
                          <div className="fui-card-content">
                            <h3 className="fui-card-title">{card.title}</h3>
                            {
                              card.description ? (
                                <div className="fui-card-description" dangerouslySetInnerHTML={{ __html: card.description }}></div>
                              ) : null
                            }
                            {
                              card.list ? (
                                <div className="fui-list">{
                                  card.list.map((item, i) => (
                                    <div className='item-with-tooltip' key={`plan-card-${idx}-item-${i}`}>
                                      <Item prefix='check'>
                                        {item.text}
                                      </Item>
                                      {
                                        item.tooltip ? (
                                          <Tooltip
                                            content={<i className='icon-information'></i>}
                                            trigger="click"
                                            tooltip={item.tooltip}
                                          />
                                        ) : null
                                      }
                                    </div>
                                  ))
                                }</div>

                              ) : null
                            }
                          </div>
                          {
                            card.action ? (
                              <div className='fui-card-extra'>
                                <Button btnStyle={card.action.btnStyle} link={card.action.link} target={card.action.target}>
                                  {card.action.text}
                                </Button>
                              </div>
                            ) : null
                          }
                        </div>
                      </div>
                    </div>
                  )
              }
            }
            )
            }
          </Slider>
        </div>
      </section>
    )
  }
}

CardFeature.propTypes = {
  title: PropTypes.string,
  titleColor: PropTypes.string,
  bgImg: PropTypes.string,
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

export default CardFeature;
```
{% endtab %}
{% endtabs %}



#### Properties

| 名稱 | 屬性 | 必填 | 選項 | 說明 |
| :--- | :--- | :--- | :--- | :--- |
| title | string | false |  |  |
| titleColor | string |  |  |  |
| bgImg | string |  |  |  |
| cards | array |  |  |  |
| type | string |  | promotion, card01 |  |
| bg | string |  | red |  |

card 形式為promotion請帶入type: promotion, 顏色  
{ "type": "promotion", "title": "好禮1+1帶走AirPods享38折，貼補你 iPhone SE 的配件費換手機一次到位", "bg": "red", "action": { "btnStyle": "primary", "text": "馬上申辦", "link": "\#", "target": "\_self" } },

