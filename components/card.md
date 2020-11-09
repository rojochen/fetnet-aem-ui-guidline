# Card

牌卡以 `<Card />` 為單位，依設計搭配不同的 section 或樣式名稱。

也可以直接使用 HTML 依照架構放入內容。若有不需要的欄位，可不帶參數或不使用該 HTML。



{% tabs %}
{% tab title="Usage" %}
```jsx

import Card from '../components/card/Card';

<Card
    className="promotion-article"
    link={'#'}
    icon='/resources/help-center/images/business-response.svg'
    title='企業用戶問題反應'
    description='有任何問題嗎? 您可立即線上填寫資料，預約專人為您服務。'
/>
```
{% endtab %}

{% tab title="Card.js" %}
```jsx
import React from 'react';
import { Link } from 'react-router-dom'
import PropTypes from 'prop-types';

const Card = props => {
    const renderCardContent = () => {
        return props.link ? (
            <Link className='fui-card-action' to={props.link}>
                {
                    props.image ? (
                        <div className="fui-card-image">
                            <img src={props.image} srcSet={props.retinaImage || props.image} alt={props.meta} />
                        </div>
                    ) : ''
                }
                <div className='fui-card-caption'>
                    <div className='fui-card-content'>
                        {
                            (!props.public_at) ? '' : (
                                <div className="fui-card-date">{props.public_at}</div>
                            )
                        }
                        {
                            (!props.meta) ? '' : (
                                <div className="fui-card-meta">{props.meta}</div>
                            )
                        }
                        <h4 className="fui-card-title">
                            {
                                (!props.icon) ? '' : (
                                    <div className='icon'>
                                        <img src={props.icon} alt={props.meta} />
                                    </div>
                                )
                            }
                            <div className='text'>
                                {props.title}
                            </div>
                        </h4>
                        {
                            (!props.description) ? '' : (
                                <p className="fui-card-description" dangerouslySetInnerHTML={{ __html: props.description }}>
                                </p>
                            )
                        }
                    </div>
                    <div className='fui-card-extra'>
                        <div className={`fui-button is-arrow mb-0 ${props.className && props.className.indexOf('promotion-article') > -1 ? 'is-reverse' : ''}`}>
                            {props.action ? props.action.text : '看更多'}
                        </div>
                    </div>
                </div>
            </Link>
        ) : (
                <div className="fui-card-action">
                    {
                        props.image ? (
                            <div className="fui-card-image">
                                <img src={props.image} srcSet={props.retinaImage || props.image} alt={props.meta} />
                            </div>
                        ) : ''
                    }
                    <div className='fui-card-caption'>
                        <div className='fui-card-content'>
                            {
                                (!props.public_at) ? '' : (
                                    <div className="fui-card-date">{props.public_at}</div>
                                )
                            }
                            {
                                (!props.meta) ? '' : (
                                    <div className="fui-card-meta">{props.meta}</div>
                                )
                            }
                            <h4 className="fui-card-title">
                                {
                                    (!props.icon) ? '' : (
                                        <div className='icon'>
                                            <img src={props.icon} alt={props.meta} />
                                        </div>
                                    )
                                }
                                {props.title}
                            </h4>
                            {
                                (!props.description) ? '' : (
                                    <p className="fui-card-description" dangerouslySetInnerHTML={{ __html: props.description }}>
                                    </p>
                                )
                            }
                        </div>
                        <div className='fui-card-extra'>
                            <div className={`fui-button is-arrow mb-0 ${props.className && props.className.indexOf('promotion-article') > -1 ? 'is-reverse' : ''}`}>
                                {props.action ? props.action.text : '看更多'}
                            </div>
                        </div>
                    </div>
                </div>
            )
    }

    return (
        <div className={`fui-card ${props.className ? props.className : ''}`}>
            {renderCardContent()}
        </div>
    )
}

Card.propTypes = {
    className: PropTypes.string,
    link: PropTypes.string,
    retinaImage: PropTypes.string,
    image: PropTypes.string,
    meta: PropTypes.string,
    icon: PropTypes.string,
    public_at: PropTypes.string,
    title: PropTypes.string.isRequired,
    description: PropTypes.string,
    action: PropTypes.shape({
        text: PropTypes.string.isRequired,
        link: PropTypes.string
    })
};

export default Card;
```
{% endtab %}

{% tab title="card.html" %}
```markup
<!-- 整張牌卡都可點擊 -->
<div class='fui-card'>
    <a href="#" class="fui-card-action">
        <div class="fui-card-image">
            <img src="..." srcSet="..." alt="..." />
        </div>
        <div class='fui-card-caption'>
            <div class='fui-card-content'>
                <div class="fui-card-meta">...</div>
                <h4 class="fui-card-title">
                    <div class='icon'>
                        <img src="" alt="" />
                    </div>
                    Title
                </h4>
                <p className="fui-card-description">
                    ...
                </p>
            </div>
            <div class='fui-card-extra'>
                <div class='fui-button is-arrow mb-0'>
                    看更多
                </div>
            </div>
        </div>
    </a>
</div>


<!-- 部分可點擊 -->
<div class='fui-card'>
    <div class="fui-card-action">
        <div class="fui-card-image">
            <img src="..." srcSet="..." alt="..." />
        </div>
        <div class='fui-card-caption'>
            <div class='fui-card-content'>
                <div class="fui-card-meta">...</div>
                <h4 class="fui-card-title">
                    <div class='icon'>
                        <img src="" alt="" />
                    </div>
                    Title
                </h4>
                <p className="fui-card-description">
                    ...
                    <a href="#">...</a>
                </p>
            </div>
            <div class='fui-card-extra'>
                <a href="#" class='fui-button is-arrow mb-0'>
                    看更多
                </a>
            </div>
        </div>
    </div>
</div>
```
{% endtab %}
{% endtabs %}

#### Properties

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x540D;&#x7A31;</th>
      <th style="text-align:left">&#x5C6C;&#x6027;</th>
      <th style="text-align:left">&#x9078;&#x9805;</th>
      <th style="text-align:left">&#x5FC5;&#x586B;</th>
      <th style="text-align:left">&#x8AAA;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">className</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        <p><code>is-document</code> 
          <br /><code>is-price-card</code> 
          <br /><code>is-simple</code> 
          <br /><code>is-tooltip</code> 
          <br /><code>service-entry</code> 
          <br /><code>box</code> 
          <br /><code>promotion-article </code>
        </p>
        <p><code>is-video</code>
        </p>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x53EF;&#x4F7F;&#x7528;&#x7684;&#x6A23;&#x5F0F;&#x540D;&#x7A31;&#xFF0C;&#x4F46;&#x9700;&#x642D;&#x914D;
        <a
        href="https://app.gitbook.com/@ajacreative/s/fetnet-1/~/drafts/-M15BRlqEZqvK-93qDf7/sections/card">section</a>&#x4F7F;&#x7528;</td>
    </tr>
    <tr>
      <td style="text-align:left">link</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x8981;&#x5C0E;&#x5165;&#x7684;&#x9023;&#x7D50;</td>
    </tr>
    <tr>
      <td style="text-align:left">image</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x724C;&#x5361;&#x5716;&#x7247;</td>
    </tr>
    <tr>
      <td style="text-align:left">retinaImage</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x5728; retina display &#x4E2D;&#x986F;&#x793A;&#x7684;&#x5716;&#x7247;</td>
    </tr>
    <tr>
      <td style="text-align:left">meta</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x5C0F;&#x6A19;</td>
    </tr>
    <tr>
      <td style="text-align:left">title</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">true</td>
      <td style="text-align:left">&#x6A19;&#x984C;</td>
    </tr>
    <tr>
      <td style="text-align:left">icon</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x6A19;&#x984C;&#x4E0A;&#x7684; icon</td>
    </tr>
    <tr>
      <td style="text-align:left">public_at</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x65E5;&#x671F;</td>
    </tr>
    <tr>
      <td style="text-align:left">description</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x63CF;&#x8FF0;</td>
    </tr>
    <tr>
      <td style="text-align:left">action</td>
      <td style="text-align:left">Object</td>
      <td style="text-align:left">
        <p>text: String</p>
        <p>link: String</p>
      </td>
      <td style="text-align:left">&#x82E5;&#x6709;&#x4F7F;&#x7528; action&#xFF0C;text &#x70BA;&#x5FC5;&#x586B;</td>
      <td
      style="text-align:left">&#x724C;&#x5361;&#x4E0A;&#x6309;&#x9215;</td>
    </tr>
  </tbody>
</table>



## BanCard

```
import BanCard from '../../components/card/BanCard';

<BanCard {...{
  image: '/resources/cbu/life-circle-slashie/images/cbu-smarthome-thumb-02.jpg',
  title: '最方便的傳聲筒，不必找紙筆，對著愛講說話即可完成音箱留言。',
  subtitle: '遠傳愛講語音助理',
  type: 'img-left',
  description: '',
  checkList: false,
  checkListArrList: '',
  action: {
    text: '探索更多愛講功能',
    link: '#',
  }
}}/>

```

#### Properties

| 名稱             | 屬性   | 選項 | 必填 | 說明                                                                                                      |
| :--------------- | :----- | :--- | :--- | :-------------------------------------------------------------------------------------------------------- |
| id               | string |      |      |                                                                                                           |
| className        | string |      |      |                                                                                                           |
| type             | string |      |      |                                                                                                           |
| retinaImage      | string |      |      |                                                                                                           |
| image            | string |      |      |                                                                                                           |
| meta             | string |      |      |                                                                                                           |
| title            | string |      | true |                                                                                                           |
| description      | string |      |      |                                                                                                           |
| checkList        | bool   |      |      |                                                                                                           |
| checkListArrList | array  |      |      |                                                                                                           |
| action           | obj    |      |      | text: PropTypes.string.isRequired,link: PropTypes.string.isRequired, target: PropTypes.string.isRequired, |


## CardCollapse1

```
import CardCollapse1 from '../../components/card/CardCollapse1';
CardCollapse1
    list={...[
        {
          title: "親職教養專家 張旭鎧 (阿鎧老師)：",
          img: { url: '/resources/cbu/img/CardCollapse1-img-01.jpg', alt: 'img-01' },
          quote: "易於使用操作便利的智慧手錶，數位教養最佳工具！只要透過手機APP，就能立即了解孩子位置，隨時與父母連絡，進行互動。",
          content: "面對琳琅滿目的數位工具，該如何選擇呢？對此，阿鎧老師說，「父母易於使用、孩子操作便利的智慧手錶是個好選擇！」 「隨身佩戴的智慧手錶，能為孩子帶來安全感，加上手錶本身就帶有時間管理的觀念」他進一步以具備定位、通話與語音助理功能的《遠傳愛講定位手錶》為例，只要透過手機APP，家長就能輕鬆與孩子所佩戴的《遠傳愛講定位手錶》配對，了解孩子位置，孩子也能隨時與父母連絡，進行互動，手錶內建的鬧鐘、提醒、問天氣等功能，也能藉此養成孩子自主學習的習慣。",
          link: "#",
        },
        {
          title: "3C 部落客 babyfans 杜小威：",
          img: { url: '/resources/cbu/img/promotion-watch-babyfans@2x.png', alt: 'img-02' },
          quote: "過年外出一度走散了，馬上開定位和打電話立刻尋找他。很推薦給孩子小的家長，可以買給小孩外出用。",
          content: "面對琳琅滿目的數位工具，該如何選擇呢？對此，阿鎧老師說，「父母易於使用、孩子操作便利的智慧手錶是個好選擇！」 「隨身佩戴的智慧手錶，能為孩子帶來安全感，加上手錶本身就帶有時間管理的觀念」他進一步以具備定位、通話與語音助理功能的《遠傳愛講定位手錶》為例，只要透過手機APP，家長就能輕鬆與孩子所佩戴的《遠傳愛講定位手錶》配對，了解孩子位置，孩子也能隨時與父母連絡，進行互動，手錶內建的鬧鐘、提醒、問天氣等功能，也能藉此養成孩子自主學習的習慣。",
          link: "#",
        },
        {
          title: "朱朱育兒日記 朱兒：",
          img: { url: '/resources/cbu/img/promotion-watch-chu@2x.png', alt: 'img-03' },
          quote: "孩子可以隨時打電話給我，我也可以確認他的安全，有急事發生孩子也可按SOS通知所有家庭成員。真的是讓我輕鬆許多。",
          content: "面對琳琅滿目的數位工具，該如何選擇呢？對此，阿鎧老師說，「父母易於使用、孩子操作便利的智慧手錶是個好選擇！」 「隨身佩戴的智慧手錶，能為孩子帶來安全感，加上手錶本身就帶有時間管理的觀念」他進一步以具備定位、通話與語音助理功能的《遠傳愛講定位手錶》為例，只要透過手機APP，家長就能輕鬆與孩子所佩戴的《遠傳愛講定位手錶》配對，了解孩子位置，孩子也能隨時與父母連絡，進行互動，手錶內建的鬧鐘、提醒、問天氣等功能，也能藉此養成孩子自主學習的習慣。",
          link: "#",
        },
        {
          title: "朱朱育兒日記 朱兒：",
          img: { url: '/resources/cbu/img/CardCollapse1-img-01.jpg', alt: 'img-01' },
          quote: "孩子可以隨時打電話給我，我也可以確認他的安全，有急事發生孩子也可按SOS通知所有家庭成員。真的是讓我輕鬆許多。",
          content: "面對琳琅滿目的數位工具，該如何選擇呢？對此，阿鎧老師說，「父母易於使用、孩子操作便利的智慧手錶是個好選擇！」 「隨身佩戴的智慧手錶，能為孩子帶來安全感，加上手錶本身就帶有時間管理的觀念」他進一步以具備定位、通話與語音助理功能的《遠傳愛講定位手錶》為例，只要透過手機APP，家長就能輕鬆與孩子所佩戴的《遠傳愛講定位手錶》配對，了解孩子位置，孩子也能隨時與父母連絡，進行互動，手錶內建的鬧鐘、提醒、問天氣等功能，也能藉此養成孩子自主學習的習慣。",
          link: "#",
        },
        {
          title: "朱朱育兒日記 朱兒：",
          img: { url: '/resources/cbu/img/CardCollapse1-img-01.jpg', alt: 'img-01' },
          quote: "孩子可以隨時打電話給我，我也可以確認他的安全，有急事發生孩子也可按SOS通知所有家庭成員。真的是讓我輕鬆許多。",
          content: "面對琳琅滿目的數位工具，該如何選擇呢？對此，阿鎧老師說，「父母易於使用、孩子操作便利的智慧手錶是個好選擇！」 「隨身佩戴的智慧手錶，能為孩子帶來安全感，加上手錶本身就帶有時間管理的觀念」他進一步以具備定位、通話與語音助理功能的《遠傳愛講定位手錶》為例，只要透過手機APP，家長就能輕鬆與孩子所佩戴的《遠傳愛講定位手錶》配對，了解孩子位置，孩子也能隨時與父母連絡，進行互動，手錶內建的鬧鐘、提醒、問天氣等功能，也能藉此養成孩子自主學習的習慣。",
          link: "#",
        },
      ]}
/>
```

#### Properties

| 名稱      | 屬性   | 選項 | 必填 | 說明                                                                                                                                                                                         |
| :-------- | :----- | :--- | :--- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| title     | string |      |      |                                                                                                                                                                                              |
| className | string |      |      |                                                                                                                                                                                              |
| list      | array  |      |      | title: PropTypes.string, img: PropTypes.string,quote: PropTypes.string,content: PropTypes.string,link: PropTypes.string,img:PropTypes.shape({url: PropTypes.string,alt: PropTypes.string,}), | \ |

## CardCollapse2
```
import CardCollapse2 from '../../components/card/CardCollapse2';
<CardCollapse2
          list={...[
        {
          title: "親職教養專家 張旭鎧 (阿鎧老師)：",
          img: { url: '/resources/cbu/img/CardCollapse1-img-01.jpg', alt: 'img-01' },
          content: "面對琳琅滿目的數位工具，該如何選擇呢？對此，阿鎧老師說，「父母易於使用、孩子操作便利的智慧手錶是個好選擇！」 「隨身佩戴的智慧手錶，能為孩子帶來安全感，加上手錶本身就帶有時間管理的觀念」他進一步以具備定位、通話與語音助理功能的《遠傳愛講定位手錶》為例，只要透過手機APP，家長就能輕鬆與孩子所佩戴的《遠傳愛講定位手錶》配對，了解孩子位置，孩子也能隨時與父母連絡，進行互動，手錶內建的鬧鐘、提醒、問天氣等功能，也能藉此養成孩子自主學習的習慣。",
        },
        {
          title: "3C 部落客 babyfans 杜小威：",
          img: { url: '/resources/cbu/img/CardCollapse1-img-01.jpg', alt: 'img-01' },
          content: "面對琳琅滿目的數位工具，該如何選擇呢？對此，阿鎧老師說，「父母易於使用、孩子操作便利的智慧手錶是個好選擇！」 「隨身佩戴的智慧手錶，能為孩子帶來安全感，加上手錶本身就帶有時間管理的觀念」他進一步以具備定位、通話與語音助理功能的《遠傳愛講定位手錶》為例，只要透過手機APP，家長就能輕鬆與孩子所佩戴的《遠傳愛講定位手錶》配對，了解孩子位置，孩子也能隨時與父母連絡，進行互動，手錶內建的鬧鐘、提醒、問天氣等功能，也能藉此養成孩子自主學習的習慣。",
        },
        {
          title: "朱朱育兒日記 朱兒：",
          img: { url: '/resources/cbu/img/CardCollapse1-img-01.jpg', alt: 'img-01' },
          content: "面對琳琅滿目的數位工具，該如何選擇呢？對此，阿鎧老師說，「父母易於使用、孩子操作便利的智慧手錶是個好選擇！」 「隨身佩戴的智慧手錶，能為孩子帶來安全感，加上手錶本身就帶有時間管理的觀念」他進一步以具備定位、通話與語音助理功能的《遠傳愛講定位手錶》為例，只要透過手機APP，家長就能輕鬆與孩子所佩戴的《遠傳愛講定位手錶》配對，了解孩子位置，孩子也能隨時與父母連絡，進行互動，手錶內建的鬧鐘、提醒、問天氣等功能，也能藉此養成孩子自主學習的習慣。",
        },
        {
          title: "朱朱育兒日記 朱兒：",
          img: { url: '/resources/cbu/img/CardCollapse1-img-01.jpg', alt: 'img-01' },
          content: "面對琳琅滿目的數位工具，該如何選擇呢？對此，阿鎧老師說，「父母易於使用、孩子操作便利的智慧手錶是個好選擇！」 「隨身佩戴的智慧手錶，能為孩子帶來安全感，加上手錶本身就帶有時間管理的觀念」他進一步以具備定位、通話與語音助理功能的《遠傳愛講定位手錶》為例，只要透過手機APP，家長就能輕鬆與孩子所佩戴的《遠傳愛講定位手錶》配對，了解孩子位置，孩子也能隨時與父母連絡，進行互動，手錶內建的鬧鐘、提醒、問天氣等功能，也能藉此養成孩子自主學習的習慣。",
        },
        {
          title: "朱朱育兒日記 朱兒：",
          img: { url: '/resources/cbu/img/CardCollapse1-img-01.jpg', alt: 'img-01' },
          content: "面對琳琅滿目的數位工具，該如何選擇呢？對此，阿鎧老師說，「父母易於使用、孩子操作便利的智慧手錶是個好選擇！」 「隨身佩戴的智慧手錶，能為孩子帶來安全感，加上手錶本身就帶有時間管理的觀念」他進一步以具備定位、通話與語音助理功能的《遠傳愛講定位手錶》為例，只要透過手機APP，家長就能輕鬆與孩子所佩戴的《遠傳愛講定位手錶》配對，了解孩子位置，孩子也能隨時與父母連絡，進行互動，手錶內建的鬧鐘、提醒、問天氣等功能，也能藉此養成孩子自主學習的習慣。",
        },
      ]}
          title="用戶真實回饋"
        />
```

#### Properties

| 名稱  | 屬性   | 選項 | 必填 | 說明                                                                                                                   |
| :---- | :----- | :--- | :--- | :--------------------------------------------------------------------------------------------------------------------- |
| title | string |      |      |                                                                                                                        |
| list  | array  |      |      | title: PropTypes.string,img: PropTypes.shape({url:PropTypes.string,alt: PropTypes.string,}),content: PropTypes.string, |

## CardMultiSteps

```
import CardMultiSteps from '../../components/card/CardMultiSteps';
<CardMultiSteps
title='3 步驟輕鬆搞定出國上網'
list={[
    {
    content: '線上或實體門市購買遠遊卡',
    bg: '/resources/cbu/roaming/roaming-step-1-bgimg.svg'
    },
    {
    content: '抵達國外當地後，將 SIM 卡裝入手機',
    bg: '/resources/cbu/roaming/roaming-step-2-bgimg.svg'
    },
    {
    content: '開啟「行動數據」及「數據漫遊」自動連結國外當地網路',
    bg: '/resources/cbu/roaming/roaming-step-3-bgimg.svg'
    }
]}
/>
```
          
#### Properties

| 名稱     | 屬性   | 選項 | 必填 | 說明                                              |
| :------- | :----- | :--- | :--- | :------------------------------------------------ |
| title    | string |      |      |                                                   |
| hasMore  | bool   |      |      |                                                   |
| list     | array  |      |      | name: PropTypes.string,content: PropTypes.string, |
| bg       | string |      |      |                                                   |
| loadMore | func   |      |      |                                                   |

## CardPhonePlan

```
import CardPhonePlan from '../../components/card/CardPhonePlan';
<CardPhonePlan
          title="CardPhonePlan"
          list={[
            {
              title: '宅在家，微上網',
              img: '/resources/cbu/img/pms-1569413376-36787289@2x.jpg',
              imgAlt: '',
              price: '月付<span class="">$1,399</span><br/>專案價<span class="is-text-error">$0</span>',
              brand: 'SAMSUNG',
              name: 'SAMSUNG Galaxy A20',
              hottag: {
                text: '0元拿手機',
                color: 'red'
              },
              tag: ['福利A品'],
            },
            {
              title: '吃到飽，小寒暄',
              img: '/resources/cbu/img/cbu-promotion-product-1@2x.jpg',
              imgAlt: '',
              price: '專案價 <span class="is-text-error">$0</span>',
              brand: 'Xiaomi',
              name: '紅米 NOTE 8T 64GB',
              hottag: {
                text: '0元拿手機',
                color: 'red'
              },
              tag: [],
            },
            {
              title: '吃到飽，暢快聊',
              img: '/resources/cbu/img/pms-1569413376-36787289@2x.jpg',
              imgAlt: '',
              unit: '專案價',
              price: '<span>專案價</span><div class="price is-text-error">$9,500</div>',
              brand: 'APPLE',
              name: 'iPhone SE 64G',
              hottag: {
                text: '熱門方案',
                color: 'red'
              },
              tag: [],
            },
            {
              title: '吃到飽，暢快聊',
              img: '/resources/cbu/img/pms-1569413376-36787289@2x.jpg',
              imgAlt: '',
              unit: '專案價',
              price: '<span class="label">商品價</span><del>$5,600</del><b class="price is-text-error">$10,500</b></div>',
              brand: 'SAMSUNG',
              name: 'SAMSUNG Galaxy A20',
              hottag: {
                text: '熱門方案',
                color: 'red'
              },
              tag: [],
            },
          ]}
        />
        ```
#### Properties

| 名稱      | 屬性   | 選項 | 必填 | 說明 |
| :-------- | :----- | :--- | :--- | :--- |
| title     | string |      |      |      |
| className | string |      |      |      |
| list      | array  |      |      |      |

## CardPlanBasic

```
import CardPlanBasic from '../../components/card/CardPlanBasic';
<CardPlanBasic
          title="CardPlanBasic"
          list={[
            {
              title: '1+1好禮獎不完，AirPods輕鬆購',
              list: [
                '上網吃到飽不限速',
                '網內免費，網外950分鐘',
                '送總額$4800GoShare騎乘金',
                'AirPods $1,990或AirPods Pro $4,690或其他優惠'
              ],
              tooltip: '此處上網用量是指您該月份帳單內所有門號的上網用量加總，各門號使用明細請至「帳單明細」查詢。',
              unit: '月租',
              price: '999',
              tag: {
                text: '熱門方案',
                color: 'red'
              },
              button: [
                {
                  title: '申辦方案',
                  link: '#',
                  target: '_self'
                }
              ]
            },
            {
              title: '1+1好禮獎不完，AirPods輕鬆購',
              list: [
                '上網吃到飽不限速',
                '網內免費，網外950分鐘',
                '送總額$4800 GoShare騎乘金',
                'AirPods $1,990或AirPods Pro $4,690或其他優惠'
              ],
              unit: '月租',
              price: '999',
              tag: {
                text: '熱門方案',
                color: 'red'
              },
              button: [
                {
                  title: '申辦方案',
                  link: '#',
                  target: '_self'
                }
              ]
            },
            {
              title: '1+1好禮獎不完，AirPods輕鬆購',
              list: [
                '上網吃到飽不限速',
                '網內免費，網外950分鐘',
                '送總額$4800 GoShare騎乘金',
                'AirPods $1,990或AirPods Pro $4,690或其他優惠'
              ],
              unit: '月租',
              price: '999',
              tag: {
                text: '熱門方案',
                color: 'red'
              },
              button: [
                {
                  title: '申辦方案',
                  link: '#',
                  target: '_self'
                }
              ]
            },
            {
              title: 'AirPods Pro只要0元',
              unit: '月租',
              price: '1399',
              list: [
                '上網吃到飽不限速',
                '網內免費，網外1300分鐘</',
                '送總額$4800GoShare騎乘金',
                'AirPods Pro $0或其他3C夯品優惠'
              ],
              button: [
                {
                  title: '申辦方案',
                  link: '#',
                  target: '_self'
                }
              ]
            }
          ]}
          bottomBg="/resources/cbu/img/cbu-goshare-bg-blue2.png"
        />
        ```
        #### Properties

| 名稱     | 屬性   | 選項 | 必填 | 說明                                                                        |
| :------- | :----- | :--- | :--- | :-------------------------------------------------------------------------- |
| title    | string |      |      |                                                                             |
| bottomBg | string |      |      |                                                                             |
| topBg    | string |      |      |                                                                             |
| list     | array  |      |      | name: PropTypes.string,content: PropTypes.string,tooltip: PropTypes.string, |


## DramaCard

```
import Card from '../../card/DramaCard';
<Card key={idx} {...{
  title: '熱騰騰人氣新劇',
  more: {
    link: '#',
    text: '更多優質好劇',
  },
  cards: [
    {
      image: '/resources/cbu/life-circle-drama/images/friday-thumbnail-04.jpg',
      title: '怪咖！文主廚',
      description: '同步跟播至第2集',
      link: '#',
    },
    {
      image: '/resources/cbu/life-circle-drama/images/friday-thumbnail-04.jpg',
      title: '無人知曉',
      description: '同步跟播至第12集',
      link: '#',
    },
    {
      image: '/resources/cbu/life-circle-drama/images/friday-thumbnail-04.jpg',
      title: '戀愛可以持續到天長地久',
      description: '全20集',
      link: '#',
    }
  ]
}} />
```

#### Properties

| 名稱        | 屬性   | 選項 | 必填 | 說明                                                                 |
| :---------- | :----- | :--- | :--- | :------------------------------------------------------------------- |
| className   | string |      |      |                                                                      |
| retinaImage | string |      |      |                                                                      |
| image       | string |      |      |                                                                      |
| alt         | string |      |      |                                                                      |
| target      | string |      |      |                                                                      |
| meta        | string |      |      |                                                                      |
| title       | string |      |      |                                                                      |
| description | string |      |      |                                                                      |
| action      | object |      |      | text: PropTypes.string.isRequired,link: PropTypes.string.isRequired, |

## ECardCollapse

```
import ECardCollapse from '../../card/ECardCollapse';
<ECardCollapse key={`simple-action-card-${i}`} {...item} color={this.props.color} lineClamp={this.props.column === 3 ? 8 : 5} />
```

#### Properties

| 名稱        | 屬性   | 選項 | 必填 | 說明                                                                                                                                                         |
| :---------- | :----- | :--- | :--- | :----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| bgStyle     | string |      |      |                                                                                                                                                              |
| color       | string |      |      |                                                                                                                                                              |
| colorcolumn | number |      |      |                                                                                                                                                              |
| cards       | array  |      |      | color: PropTypes.string,titleImage: PropTypes.string, title: PropTypes.string.isRequired, description: PropTypes.string.isRequired, action: PropTypes.string |


## ECardPrice

```
import ECardPrice from '../../card/ECardPrice';
<ECardPrice key={`price-card-${i}`} {...card} />
```
#### Properties

| 名稱  | 屬性   | 選項 | 必填 | 說明                           |
| :---- | :----- | :--- | :--- | :----------------------------- |
| title | string |      |      |                                |
| cards | array  |      |      | PropTypes.objectOf(ECardPrice) |


## fCoinCard

```
import Card from '../../card/fCoinCard';
<Card key={idx} {...card} 
                fetKey={props['tracking-prefix'] ? 
                  `${props['tracking-prefix']}${props.title || ''}${props.position || ''}_${card.title || ''}${idx + 1}` 
                  : ""}/>
```
                  
| 名稱              | 屬性   | 選項 | 必填 | 說明                                           |
| :---------------- | :----- | :--- | :--- | :--------------------------------------------- |
| id                | string |      |      |                                                |
| subtitle          | string |      |      |                                                |
| title             | string |      |      |                                                |
| price             | string |      |      |                                                |
| cards             | array  |      |      | PropTypes.objectOf(Card)                       |
| bgStyle           | string |      |      |                                                |
| more              | object |      |      | text: PropTypes.string, link: PropTypes.string |
| 'tracking-prefix' | string |      |      |                                                |
| position          | number |      |      |                                                |

## FlatCard

```
import FlatCard from '../../card/FlatCard';
<FlatCard key={`box-card-${i}`} {...card} className={`box ${card.bg}`} />
```

#### Properties

| 名稱        | 屬性   | 選項 | 必填 | 說明 |
| :---------- | :----- | :--- | :--- | :--- |
| className   | string |      |      |      |
| link        | string |      |      |      |
| retinaImage | string |      |      |      |
| image       | string |      |      |      |
| icon        | string |      |      |      |
| title       | string |      | true |      |
| description | string |      |      |      |


## GoodsCard
```
import Card from '../../card/GoodsCard';
<Card key={idx} {...card} 
                fetKey={props['tracking-prefix'] ? 
                `${props['tracking-prefix']}${props.title || ''}${props.position || ''}_${card.title || ''}${idx + 1}` 
                : ""}/>
                ```
                #### Properties
```

| 名稱        | 屬性   | 選項 | 必填 | 說明                                                                 |
| :---------- | :----- | :--- | :--- | :------------------------------------------------------------------- |
| className   | string |      |      |                                                                      |
| link        | string |      |      |                                                                      |
| retinaImage | string |      |      |                                                                      |
| image       | string |      |      |                                                                      |
| target      | string |      |      |                                                                      |
| alt         | string |      |      |                                                                      |
| meta        | string |      |      |                                                                      |
| title       | string |      | true |                                                                      |
| description | string |      |      |                                                                      |
| price       | string |      |      |                                                                      |
| tag         | array  |      |      | color: PropTypes.string, text: PropTypes.string,                     |
| action      | obj    |      |      | text: PropTypes.string.isRequired, link:PropTypes.string.isRequired, |


## LifeCircleCard

```
import Card from '../../card/LifeCircleCard';
<Card key={idx} {...{
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

| 名稱        | 屬性   | 選項 | 必填 | 說明                                                                 |
| :---------- | :----- | :--- | :--- | :------------------------------------------------------------------- |
| className   | obj    |      |      |                                                                      |
| link        | string |      |      |                                                                      |
| retinaImage | string |      |      |                                                                      |
| image       | string |      |      |                                                                      |
| meta        | string |      |      |                                                                      |
| title       | string |      |      |                                                                      |
| description | string |      |      |                                                                      |
| action      | obj    |      |      | text: PropTypes.string.isRequired,link: PropTypes.string.isRequired, |


## MultiRadioCard

```
import MultiRadioCard from '../../components/card/MultiRadioCard'
<MultiRadioCard
          title="付費應用程式"
          option1={[
            { value: '1', label: '一二三四五六七八九十一二', price: 149, link: '/promotion-module' },
            { value: '2', label: '90天-愛講專案加贈 7 天', price: 447, link: '#12' },
            { value: '3', label: '180天-愛講專案加贈 15 天', price: 894, link: '#13' },
            { value: '4', label: '365天-愛講專案加贈 45 天', price: 1788, link: '#14' },
          ]}
          option2={[
            { value: '1', label: '月租無限聽_愛講專案優惠', price: 149, link: '#21' },
            { value: '2', label: '90天-愛講專案加贈 7 天', price: 447, link: '#22' },
            { value: '3', label: '180天-愛講專案加贈 15 天', price: 894, link: '#23' },
            { value: '4', label: '365天-愛講專案加贈 45 天', price: 1788, link: '#24' },
          ]}
          list={[
            {
              title: '一二三四五六七八九十',
            },
            {
              title: 'KKBOX',
            }
          ]}
          form={{
            options1: { value: '1', required: false },
            options2: { value: '1', required: false },
          }}
        />
```

#### Properties

| 名稱    | 屬性   | 選項 | 必填 | 說明                                                                                            |
| :------ | :----- | :--- | :--- | :---------------------------------------------------------------------------------------------- |
| title   | string |      |      |                                                                                                 |
| option1 | array  |      |      | value: PropTypes.string,label:PropTypes.string, price: PropTypes.number,link: PropTypes.string, |
| option2 | array  |      |      | value: PropTypes.string,label:PropTypes.string, price: PropTypes.number,link: PropTypes.string, |
| list    | array  |      |      | title: PropTypes.string,                                                                        |
| form    | obj    |      |      | options1: PropTypes.shape({value: PropTypes.string,required: PropTypes.bool,}),                 |


## ProdPromoCard

```
import ProdPromoCard from '../../components/card/ProdPromoCard';
<ProdPromoCard {...{
        total: 0,
        list: [],
        current: 0,
        perPage: 12,
        pages: 0
      }} key={`find-prod-${i}`} />
```

#### Properties

| 名稱    | 屬性   | 選項 | 必填 | 說明 |
| :------ | :----- | :--- | :--- | :--- |
| total   | number |      |      |      |
| list    | string |      |      |      |
| current | number |      |      |      |
| perPage | number |      |      |      |
| pages   | number |      |      |      |


## ProductCard

```
import ProductCard from '../../card/ProductCard'
<ProductCard {...[
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
  ]}  key={`fui-promo-prod-section-content-${i}-card-${j}`} />
```

| 名稱         | 屬性   | 選項 | 必填 | 說明 |
| :----------- | :----- | :--- | :--- | :--- |
| image        | string |      |      |      |
| ribbon       | string |      |      |      |
| meta         | string |      |      |      |
| title        | string |      |      |      |
| tag          | string |      |      |      |
| salePrice    | string |      |      |      |
| projectPrice | string |      |      |      |
| originPrice  | string |      |      |      |

## ProductCardWithMultiAction

```
import ProductCardWithMultiAction from '../../card/ProductCardWithMultiAction';
<ProductCardWithMultiAction key={`product-result-${i}`} type='product' {...[
  {
    ribbon: '網路限定優惠',
    image: '/resources/cbu/search-result/product-1.png',
    retinaImage: '/resources/cbu/search-result/product-1@2x.png',
    title: 'Apple iPad Pro 11 LTE 256GB (2018)',
    meta: 'Apple',
    link: '#',
    target: '_blank',
    actions: [
      {
        link: '#',
        target: '_blank',
        icon: 'buy',
        text: '購買'
      }
    ]
  },
  {
    ribbon: '新機上市',
    image: '/resources/cbu/search-result/product-2.png',
    retinaImage: '/resources/cbu/search-result/product-2@2x.png',
    title: 'Apple iPhone 11 Pro 64GB福利品',
    meta: 'Apple',
    link: '#',
    target: '_blank',
    actions: [
      {
        link: '#',
        target: '_blank',
        icon: 'buy',
        text: '購買'
      }
    ]
  },
  {
    image: '/resources/cbu/search-result/product-3.png',
    retinaImage: '/resources/cbu/search-result/product-3@2x.png',
    title: 'Apple iPhone SE 64GB 2020',
    meta: 'Apple',
    link: '#',
    target: '_blank',
    actions: [
      {
        link: '#',
        target: '_blank',
        icon: 'buy',
        text: '購買'
      }
    ]
  }
]} />
```

| 名稱        | 屬性   | 選項 | 必填 | 說明                                                                                            |
| :---------- | :----- | :--- | :--- | :---------------------------------------------------------------------------------------------- |
| type        | string |      |      |                                                                                                 |
| link        | string |      |      |                                                                                                 |
| target      | string |      |      |                                                                                                 |
| ribbon      | string |      |      |                                                                                                 |
| image       | string |      |      |                                                                                                 |
| retinaImage | string |      |      |                                                                                                 |
| title       | string |      |      |                                                                                                 |
| meta        | string |      |      |                                                                                                 |
| description | string |      |      |                                                                                                 |
| actions     | obj    |      |      | link: PropTypes.string, icon: PropTypes.string, text: PropTypes.string,target: PropTypes.string |

## ProductListCard

```
import Card from '../../card/ProductListCard';
<Card key={idx} {...{
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
    },} />
```

| 名稱      | 屬性   | 選項 | 必填 | 說明                                                                  |
| :-------- | :----- | :--- | :--- | :-------------------------------------------------------------------- |
| className | string |      |      |                                                                       |
| tag       | obj    |      |      | color: PropTypes.string, text: PropTypes.string,                      |
| title     | string |      |      |                                                                       |
| image     | string |      |      |                                                                       |
| lists     | obj    |      |      | text: PropTypes.string,                                               |
| action    | obj    |      |      | text: PropTypes.string.isRequired, link: PropTypes.string.isRequired, |

## PromotionCard
```
import PromotionCard from '../../components/partials/PromotionCard';
topBg={null}
bottomBg={this.state.coopBg}
program={this.state.program}
/>
```
| 名稱     | 屬性   | 選項 | 必填 | 說明 |
| :------- | :----- | :--- | :--- | :--- |
| topBg    | string |      |      |      |
| bottomBg | string |      |      |      |
| props    | string |      |      |      |

## RoamingCard

```
import Card from '../../components/card/RoamingCard';
<Card
              key={`card-roaming-multi-${j}`}
              openModal={this.openModal}
              {...card}
              defaultImg={this.props.defaultImg || ""}
              isAircraft={this.props.isAircraft || false}
            />
```
            
| 名稱      | 屬性   | 選項 | 必填 | 說明                                                                      |
| :-------- | :----- | :--- | :--- | :------------------------------------------------------------------------ |
| image     | string |      |      |                                                                           |
| imgAlt    | string |      |      |                                                                           |
| title     | string |      |      |                                                                           |
| price     | string |      |      |                                                                           |
| desc      | string |      |      |                                                                           |
| target    | string |      |      |                                                                           |
| country   | string |      |      |                                                                           |
| price     | string |      |      |                                                                           |
| modalText | string |      |      |                                                                           |
| modal     | obj    |      |      | title: PropTypes.string, content: PropTypes.any,                          |
| tag       | obj    |      |      | text: PropTypes.string, color: PropTypes.string,                          |
| button    | obj    |      |      | text: PropTypes.string, target: PropTypes.string, link: PropTypes.string, |
| openModal | func   |      |      |                                                                           |

## SectionCard2

```
import SectionCard2 from '../../components/card/SectionCard2'
<SectionCard2
          title="更多貼心服務"
          tabs={[
            { name: '01', label: '音樂、有聲書', text: '音樂、有聲書', value: '音樂、有聲書', index: 0 },
            { name: '02', label: '新聞廣播', text: '新聞廣播', value: '新聞廣播', index: 1 },
            { name: '03', label: '資訊快查', text: '資訊快查', value: '資訊快查', index: 2 },
            { name: '04', label: '生活幫手1', text: '生活幫手1', value: '生活幫手1', index: 3 },
            { name: '05', label: '生活幫手2', text: '生活幫手2', value: '生活幫手2', index: 4 },
            { name: '06', label: '生活幫手3', text: '生活幫手3', value: '生活幫手3', index: 5 },
          ]}
          list={[
            [
              {
                meta: '一二三四五六七八九十一二三四五六七八九', title: '一二三四五六七八九十一二', content: '一二三四五六七八九十一二三四五六七八九十一二三四五六七八九十一二三四五六七八九十一二三四五六七八九十一', tips: '一二三四五六七八九十一二三四五六七八九十一二'
              },
              {
                meta: '音樂雙平台', title: 'KKBOX音樂', content: '聽音樂的好朋友，在愛講、電腦、手機等隨處都能享受千萬首正版好音樂。', tips: '聲控 Tips：來首蘇打綠的歌、我想聽周杰倫'
              },
              {
                meta: '有聲書', title: '樂學有聲書', content: '含近千則故事及兒歌，提升孩子想像力及創造力，培養藝術及閱讀素養。', tips: '聲控 Tips：我想聽狐狸請客的故事'
              },
              {
                meta: '有聲書', title: '愛播聽書FM', content: '童書、娛樂、人文、百科等自由選聽，囊括最多台灣名家的有聲知識內容。', tips: '聲控 Tips：我要聽愛播(兒童故事/老人與海)'
              },
              {
                meta: '英語學習', title: '空中英語教室 每日一句', content: '一天一句，輕鬆學英文，週一~週五每天給您不一樣的內容，週末隨選週間內容重播複習。', tips: '聲控 Tips：我想聽空英每日一句'
              },
              {
                meta: '音樂雙平台', title: 'KKBOX音樂', content: '聽音樂的好朋友，在愛講、電腦、手機等隨處都能享受千萬首正版好音樂。', tips: '聲控 Tips：來首蘇打綠的歌、我想聽周杰倫'
              },
            ],
            [
              {
                meta: '音樂雙平台', title: 'KKBOX音樂', content: '聽音樂的好朋友，在愛講、電腦、手機等隨處都能享受千萬首正版好音樂。', tips: '聲控 Tips：來首蘇打綠的歌、我想聽周杰倫'
              },
              {
                meta: '音樂雙平台', title: 'KKBOX音樂', content: '聽音樂的好朋友，在愛講、電腦、手機等隨處都能享受千萬首正版好音樂。', tips: '聲控 Tips：來首蘇打綠的歌、我想聽周杰倫'
              }
            ],
            [
              {
                meta: '音樂雙平台', title: 'KKBOX音樂', content: '聽音樂的好朋友，在愛講、電腦、手機等隨處都能享受千萬首正版好音樂。', tips: '聲控 Tips：來首蘇打綠的歌、我想聽周杰倫'
              },
              {
                meta: '音樂雙平台', title: 'KKBOX音樂', content: '聽音樂的好朋友，在愛講、電腦、手機等隨處都能享受千萬首正版好音樂。', tips: '聲控 Tips：來首蘇打綠的歌、我想聽周杰倫'
              }
            ],
          ]}
        />
```

| 名稱 | 屬性  | 選項 | 必填 | 說明 |
| :--- | :---- | :--- | :--- | :--- |
| list | array |      |      |      |
| tabs | array |      |      |      |

## ServiceEntry

```
import ServiceEntry from '../../components/partials/card/ServiceEntry'
{
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
}
```

| 名稱  | 屬性   | 選項 | 必填 | 說明                                            |
| :---- | :----- | :--- | :--- | :---------------------------------------------- |
| title | string |      |      |                                                 |
| cards | array  |      |      | title: PropTypes.string, link: PropTypes.string |


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

| 名稱        | 屬性   | 選項 | 必填 | 說明                                         |
| :---------- | :----- | :--- | :--- | :------------------------------------------- |
| title       | string |      |      |                                              |
| description | string |      |      |                                              |
| className   | string |      |      |                                              |
| icon        | string |      |      |                                              |
| switch      | array  |      |      | on: PropTypes.string, off: PropTypes.string, |

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

| 名稱  | 屬性   | 選項 | 必填 | 說明                                                                                                                                                                  |
| :---- | :----- | :--- | :--- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| title | string |      |      |                                                                                                                                                                       |
| cards | string |      |      | image: PropTypes.string,retinaImage: PropTypes.string,title: PropTypes.string,description: PropTypes.string,link: PropTypes.string,target: PropTypes.string, // _self |  | _blank |