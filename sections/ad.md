# Ad

### section-ad-1

全站型橫幅廣告模組, 可放置在首頁、產品頁、企業解決方案. 可依需求編輯欄位:  
1. 大標: 最大字符串長度&lt;60 \(60個字元\), 建議最多1行  
2. 按鈕: 可以依需求選擇1-2個按鈕, 文字最大字符串長度&lt;20 \(20個字元\)  
3. 大網背景圖 \(1440x200px\) • 小網背景圖\(16:9\)  
小網隨字串長度跟著延展section高度

{% tabs %}
{% tab title="Web" %}
![](../.gitbook/assets/image%20%2892%29.png)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/image%20%28268%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Web" %}
![](../.gitbook/assets/image%20%28136%29.png)

大標\(27個字元\) + 主按鈕\(20個字元\) + 副按鈕\(8個字元\)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/image%20%2890%29.png)

小網按鈕文字過長時, 會自動向下並排
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Web" %}
![](../.gitbook/assets/image%20%28175%29.png)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/image%20%2886%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Usage" %}
```jsx
import SectionAd1 from '../components/partials/SectionAd1';

<SectionAd1
  image={{
    md: '/resources/ebu/images/ebu-micro-ad-01.jpg',
    sm: '/resources/ebu/images/ebu-micro-ad-01.jpg',
  }}
  title={`遠傳嚴選系列「頭家輕鬆配」超值產品及服務`}
  action={[
    {
      text: '了解更多',
      line: '#',
      btnStyle: 'secondary',
    },
  ]}
/>
```
{% endtab %}

{% tab title="SectionAd1" %}
```jsx
import React from 'react';
import { Grid } from '@material-ui/core';
import Button from '../Button';
import PropTypes from 'prop-types';

const SectionAd1 = props => {
  const [isMd, setIsMd] = React.useState(window.innerWidth > 768);

  React.useEffect(() => {
    window.onresize = () => {
      setIsMd(window.innerWidth > 768);
    };
  });

  return (
    <section
      className='fui-section-promo'
      style={{
        backgroundImage: `url(${isMd ? props.image.md : props.image.sm})`,
      }}>
      <div className='fui-container'>
        <Grid container justify='center'>
          <Grid item xs={12} sm={12} md={6} className='content'>
            <h4 className='fui-section-promo-title' dangerouslySetInnerHTML={{ __html: props.title }}></h4>
          </Grid>
          <Grid item xs={12} sm={12} md={6} className='action'>
            {props.action.map((act, i) => (
              <Button
                link={act.link}
                key={`ad-action-${i}`}
                btnStyle={act.btnStyle || 'secondary'}
                reverse={true}>
                {act.text}
              </Button>
            ))}
          </Grid>
        </Grid>
      </div>
    </section>
  );
};

SectionAd1.propTypes = {
  image: PropTypes.shape({
    md: PropTypes.string,
    sm: PropTypes.string,
  }),
  title: PropTypes.string,
  action: PropTypes.arrayOf(
    PropTypes.shape({
      text: PropTypes.string,
      link: PropTypes.string,
      btnStyle: PropTypes.string, // only 'primary' or 'secondary
    })
  ),
};

export default SectionAd1;

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
      <td style="text-align:left">image</td>
      <td style="text-align:left">Object</td>
      <td style="text-align:left">true</td>
      <td style="text-align:left">
        <p>{</p>
        <p>md,</p>
        <p>sm</p>
        <p>}</p>
      </td>
      <td style="text-align:left">&#x8F38;&#x5165;&#x6846;&#x540D;&#x7A31;</td>
    </tr>
    <tr>
      <td style="text-align:left">title</td>
      <td style="text-align:left">HTML</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x6A19;&#x984C;&#xFF0C;&#x53EF;&#x4F7F;&#x7528; HTML</td>
    </tr>
    <tr>
      <td style="text-align:left">actions</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>{</p>
        <p>text: String,</p>
        <p>link: String,</p>
        <p>btnStyle: String</p>
        <p>}</p>
      </td>
      <td style="text-align:left">
        <p>text: &#x6309;&#x9215;&#x6587;&#x5B57;</p>
        <p>link: &#x6309;&#x9215;&#x9023;&#x7D50;</p>
        <p>btnStyle: &#x53C3;&#x8003; <a href="https://app.gitbook.com/@ajacreative/s/fetnet-1/~/drafts/-M1UcXqTKllWDo7NORNq/v/master/elements/button">Button</a>&#xFF0C;
          <br
          />&#x53EF;&#x4F7F;&#x7528; <code>primary</code> &#x548C; <code>secondary</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>

### section-ad-2

活動型橫幅廣告模組, 建議使用在線上或線下活動需求, 可放置在首頁、產品頁、企業解決方案.   
可依需求編輯欄位:  
1. 大標: 最大字符串長度&lt;20 \(20個字元\), 建議最多1行  
2. 副標: 最大字符串長度&lt;50 \(50個字元\), 建議最多1行  
3. 按鈕: 文字最大字符串長度&lt;20 \(20個字元\). • 大網背景圖 \(1440x200px\)  
4. 小網背景圖\(16:9\)   
  
小網隨字串長度跟著延展section高度

{% tabs %}
{% tab title="Usage" %}
```jsx
import SectionAd2 from '../components/partials/SectionAd2';

<SectionAd2
  image={{
    md: '/resources/ebu/images/ebu-micro-ad-01.jpg',
    sm: '/resources/ebu/images/ebu-micro-ad-01-sm.jpg',
  }}
  title='2020開店進化論'
  description='業界大師不藏私傳授經營心法業界大師不藏私傳授經營心'
  action={{
    text: '追蹤 FB',
    line: '#',
  }}
/>
```
{% endtab %}

{% tab title="SectionAd2" %}
```jsx
import React from 'react';
import { Grid } from '@material-ui/core';
import Button from '../Button'
import PropTypes from 'prop-types';

const SectionAd2 = (props) => {
    const [isMd, setIsMd] = React.useState(window.innerWidth > 768);

    window.onresize = () => {
        setIsMd(window.innerWidth > 768)
    }

    return (
        <section className="fui-section-promo with-pattern"
            style={{
                backgroundImage: `url(${isMd ? props.image.md : props.image.sm})`
            }}>
            <div className="fui-container">
                <Grid container justify="center">
                    <Grid item xs={12} sm={12} md={6} className='content'>
                        <div className="section-of-promotion-2">
                            <h4 className="fui-section-promo-title" dangerouslySetInnerHTML={{ __html: props.title }}>
                            </h4>
                            {
                                props.description ? (
                                    <p>
                                        {props.description}
                                    </p>
                                ) : ''
                            }
                        </div>
                    </Grid>
                    <Grid item xs={12} sm={12} md={6} className='action'>
                        {
                            <Button link={props.action.link} btnStyle={props.action.btnStyle || 'secondary'} reverse={true}>
                                {props.action.text}
                            </Button>
                        }
                    </Grid>
                </Grid>
            </div>
        </section>
    );
}

SectionAd2.propTypes = {
    image: PropTypes.shape({
        md: PropTypes.string,
        sm: PropTypes.string
    }),
    title: PropTypes.string,
    description: PropTypes.string,
    action: PropTypes.shape({
        text: PropTypes.string,
        link: PropTypes.string,
        btnStyle: PropTypes.string // only 'primary' or 'secondary
    })
}

export default SectionAd2;

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
      <td style="text-align:left">image</td>
      <td style="text-align:left">Object</td>
      <td style="text-align:left">true</td>
      <td style="text-align:left">
        <p>{</p>
        <p>md,</p>
        <p>sm</p>
        <p>}</p>
      </td>
      <td style="text-align:left">&#x8F38;&#x5165;&#x6846;&#x540D;&#x7A31;</td>
    </tr>
    <tr>
      <td style="text-align:left">title</td>
      <td style="text-align:left">HTML</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x6A19;&#x984C;&#xFF0C;&#x53EF;&#x4F7F;&#x7528; HTML</td>
    </tr>
    <tr>
      <td style="text-align:left">description</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x526F;&#x6A19;&#x984C;&#xFF0C;&#x7D14;&#x5B57;&#x4E32;</td>
    </tr>
    <tr>
      <td style="text-align:left">actions</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>{</p>
        <p>text: String,</p>
        <p>link: String,</p>
        <p>btnStyle: String</p>
        <p>}</p>
      </td>
      <td style="text-align:left">
        <p>text: &#x6309;&#x9215;&#x6587;&#x5B57;</p>
        <p>link: &#x6309;&#x9215;&#x9023;&#x7D50;</p>
        <p>btnStyle: &#x53C3;&#x8003; <a href="https://app.gitbook.com/@ajacreative/s/fetnet-1/~/drafts/-M1UcXqTKllWDo7NORNq/v/master/elements/button">Button</a>&#xFF0C;
          <br
          />&#x53EF;&#x4F7F;&#x7528; <code>primary</code> &#x548C; <code>secondary</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>

{% tabs %}
{% tab title="Web" %}
![](../.gitbook/assets/image%20%28264%29.png)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/image%20%28248%29.png)
{% endtab %}
{% endtabs %}

### section-ad-3

文字型橫幅廣告模組, 建議使用作為客服或幫助中心的引導區塊, 建議與上方section內容有連續性或關聯性, 可依需求編輯欄位：  
1. 大標: 最大字符串長度&lt;60 \(60個字元\), 建議最多1行   
2. 按鈕: 可以依需求選擇1-2個按鈕, 文字最大字符串長度&lt;20 \(20個字元\)  
3. 2種模板style選擇

小網section高度規則: 最小180px, 最大261px

{% tabs %}
{% tab title="Web" %}
  
**Darkgray**

![](../.gitbook/assets/image%20%28208%29.png)

**Darkgray**

![](../.gitbook/assets/image%20%2891%29.png)
{% endtab %}

{% tab title="Mobile" %}
**Blue**

![](../.gitbook/assets/image%20%28238%29.png)

**Darkgray**

![](../.gitbook/assets/image%20%28101%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Web" %}
**Blue**

![](../.gitbook/assets/image%20%28180%29.png)

**Darkgray**

![](../.gitbook/assets/image%20%2822%29.png)
{% endtab %}

{% tab title="Mobile" %}
**Blue**

![](../.gitbook/assets/image%20%28250%29.png)

**Darkgray**

![](../.gitbook/assets/image%20%2857%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Usage" %}
```jsx
import SectionAd3 from '../components/partials/SectionAd3';

<SectionAd3
  patternColor='gray'
  title={`開業技法新知，盡在【創業開店好幫手】粉絲團`}
  action={[
    {
      text: '追蹤 FB',
      link: '#',
    },
    {
      text: '追蹤 IG',
      link: '#',
    },
  ]}
/>
```
{% endtab %}

{% tab title="SectionAd3" %}
```jsx
import React from 'react';
import { Grid } from '@material-ui/core';
import { Link } from 'react-router-dom';
import PropTypes from 'prop-types';

const SectionAd3 = props => {
  return (
    <section className={`fui-section-promo bg-pattern-${props.patternColor}`}>
      <div className='fui-container'>
        <Grid container justify='center'>
          <Grid item xs={12} sm={12} md={6} className='content'>
            <h4 className='fui-section-promo-title' dangerouslySetInnerHTML={{ __html: props.title }}></h4>
          </Grid>
          <Grid item xs={12} sm={12} md={6} className='action'>
            {props.action.map((act, i) => (
              <Link
                key={`ad-action-${i}`}
                to='#'
                className={`fui-button ${
                  act.btnStyle === 'primary' ? 'is-primary' : 'is-secondary'
                } is-medium is-reverse`}>
                <span className='text'>{act.text}</span>
              </Link>
              // <Link to={act.link} key={`ad-action-${i}`} className={act.btnStyle || 'secondary'} size="medium" reverse={true}>
              //     {act.text}
              // </Link>
            ))}
          </Grid>
        </Grid>
      </div>
    </section>
  );
};

SectionAd3.propTypes = {
  patternColor: PropTypes.string, // only 'blue' or 'gray'
  title: PropTypes.string,
  action: PropTypes.arrayOf(
    PropTypes.shape({
      text: PropTypes.string,
      link: PropTypes.string,
      btnStyle: PropTypes.string, // only 'primary' or 'secondary
    })
  ),
};

export default SectionAd3;

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
      <td style="text-align:left">patternColor</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p><code>gray</code>
        </p>
        <p><code>blue</code>
        </p>
      </td>
      <td style="text-align:left">&#x9078;&#x64C7;&#x80CC;&#x666F;&#x984F;&#x8272;</td>
    </tr>
    <tr>
      <td style="text-align:left">image</td>
      <td style="text-align:left">Object</td>
      <td style="text-align:left">true</td>
      <td style="text-align:left">
        <p>{</p>
        <p>md,</p>
        <p>sm</p>
        <p>}</p>
      </td>
      <td style="text-align:left">&#x8F38;&#x5165;&#x6846;&#x540D;&#x7A31;</td>
    </tr>
    <tr>
      <td style="text-align:left">title</td>
      <td style="text-align:left">HTML</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x6A19;&#x984C;&#xFF0C;&#x53EF;&#x4F7F;&#x7528; HTML</td>
    </tr>
    <tr>
      <td style="text-align:left">actions</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>{</p>
        <p>text: String,</p>
        <p>link: String,</p>
        <p>btnStyle: String</p>
        <p>}</p>
      </td>
      <td style="text-align:left">
        <p>text: &#x6309;&#x9215;&#x6587;&#x5B57;</p>
        <p>link: &#x6309;&#x9215;&#x9023;&#x7D50;</p>
        <p>btnStyle: &#x53C3;&#x8003; <a href="https://app.gitbook.com/@ajacreative/s/fetnet-1/~/drafts/-M1UcXqTKllWDo7NORNq/v/master/elements/button">Button</a>&#xFF0C;
          <br
          />&#x53EF;&#x4F7F;&#x7528; <code>primary</code> &#x548C; <code>secondary</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>

### section-ad-4

Megamenu廣告模組, 可依需求編輯欄位:  
1. 大標: 最大字符串長度&lt;40 \(40個字元\), 建議最多3行   
2. 小標: 最大字符串長度&lt;60 \(60個字元\), 建議最多3行   
3. 按鈕: 文字最大字符串長度&lt;20 \(20個字元\)

{% tabs %}
{% tab title="Web" %}
![](../.gitbook/assets/image%20%28237%29.png)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/image%20%28105%29.png)
{% endtab %}
{% endtabs %}

程式碼同 SectionAd5

### section-ad-5

側邊欄廣告模組, 可依需求編輯欄位:  
1. 大標: 最大字符串長度&lt;40 \(40個字元\)  
2. 小標: 最大字符串長度&lt;60 \(60個字元\)  
3. 按鈕: 文字最大字符串長度&lt;20 \(20個字元\)

{% tabs %}
{% tab title="Web" %}
![](../.gitbook/assets/image%20%28107%29.png)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/image%20%2876%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Usage" %}
```jsx
import SectionAd5 from '../../ad/SectionAd5';

// In megamenu
<div className='menu-extra' key={`menu-extra-${i}`}>
    <SectionAd5 {...menuItem.content.commercial} />
</div>

// In Sidebar
<Grid item xs={12} sm={12} md={4}>
  <div>
    <SectionAd5 {...PerformanceMock.promotion} />
  </div>
</Grid>
```
{% endtab %}

{% tab title="SectionAd5" %}
```jsx
import React from 'react';
import PropTypes from 'prop-types';
import { Link } from 'react-router-dom';

class SectionAd5 extends React.Component {
  render() {
    return (
      <div className='section-promotion-5'>
        <Link to={this.props.action.link}
          style={{ backgroundImage: `url(${this.props.image})` }}
        >
          <div className='desktop'>
            <h3>{this.props.title}</h3>
            <h6>{this.props.content}</h6>
            <div className='promotion-button'>
              <span className="text" dangerouslySetInnerHTML={{ __html: this.props.action.text || '了解更多' }} />
            </div>
          </div>
          <div className='mobile'>
            <h3>{this.props.title}</h3>
            <h6>{this.props.content}</h6>
            <div className='promotion-button'>
              <span className="text" dangerouslySetInnerHTML={{ __html: this.props.action.text || '了解更多' }} />
            </div>
          </div>
        </Link>
      </div>
    );
  }
}

SectionAd5.propTypes = {
  image: PropTypes.string,
  title: PropTypes.string,
  content: PropTypes.string,
  action: PropTypes.shape({
    text: PropTypes.string,
    link: PropTypes.string,
  }),
};

export default SectionAd5;

```
{% endtab %}

{% tab title="Mock" %}
```jsx
export const promotion = {
  image: '/resources/ebu/images/sidebar-promotion-demo.jpg',
  title: '遠傳企業Office 365 輕享方案',
  content: '最殺的價格、超彈性的付費、完整雲端行動辦公，一次幫你搞定！',
  action: {
    link: '#',
    text: '了解更多',
  },
};

```
{% endtab %}
{% endtabs %}

### section-ad-6

牌卡型廣告模組, 最多顯示3則牌卡, 可依需求編輯欄位:  
1. 大標: 最大字符串長度&lt;40 \(40個字元\), 建議最多2行  
2. 小標: 最大字符串長度&lt;60 \(60個字元\), 建議最多2行

{% tabs %}
{% tab title="Web" %}
![](../.gitbook/assets/image%20%2859%29.png)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/image%20%2872%29.png)
{% endtab %}
{% endtabs %}

此廣告區塊尚無共用，未做成模組，未來若需改寫為獨立 請參考 SearchResult.js。

{% tabs %}
{% tab title="Usage" %}
```jsx
import Card from '../components/card/Card';


{this.filterData().map((item, i) => (
  <div key={`result-item-${i}`} className='result-item'>
    <Link to={item.link} className='result-content'>
      <h6 className='result-header'>
        ...
      </h6>
      <p
        ...
    </Link>
    // 從此處放入廣告
    {item.extra ? (
      <div className='result-extra'>
        <div className='fui-cards three-card'>
          {item.extra.map((card, j) => (
            <Card key={`result-item-${i}-extra-${j}`} {...card} />
          ))}
        </div>
      </div>
    ) : (
      ''
    )}
  </div>
))}
```
{% endtab %}

{% tab title="Mock" %}
```jsx
export const resultList = [
   {
      ...,
      extra: [
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
    ],
   }
]
```
{% endtab %}
{% endtabs %}

