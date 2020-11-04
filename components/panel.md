# Panel

Panel

預設panel樣式，不帶任何元素，PanelContent 的元件與任何 HTML 元素都可放入。

{% tabs %}
{% tab title="Web" %}
![](../.gitbook/assets/image%20%2860%29.png)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/image%20%2821%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Usage" %}
```jsx
import Panel from '../components/panel/Panel';

<Panel>
    /** 
        Panel Content 
    **/
</Panel>
```
{% endtab %}

{% tab title="Panel.js" %}
```jsx
import React from 'react';

import PropTypes from 'prop-types';

class Panel extends React.Component {
    render() {
        return (
            <div className="fui-panel">
                {this.props.children}
            </div>
        )
    }
}

Panel.propTypes = {
    children: PropTypes.any.isRequired
}

export default Panel;
```
{% endtab %}
{% endtabs %}

#### Properties

| 名稱 | 屬性 | 必填 | 選項 | 說明 |
| :--- | :--- | :--- | :--- | :--- |
| children  | Node |  | \`\` | 可輸入 HTML 或下方其他 PanelContent的模組 |

## CollapsePanel

多了擴展收合按鈕的 panel 樣式，需獨立使用不可包入 Panel 中。   
  
展開的樣式設計可以依需求調整：  
1. 大標 \(固定寬度內不限字數\)   
2. 小標 \(同 panel-title-2模組\)   
3. 內文或條列項目

{% tabs %}
{% tab title="Web" %}
收合樣式

![](../.gitbook/assets/image%20%2873%29.png)

展開樣式

![](../.gitbook/assets/image%20%28122%29.png)
{% endtab %}

{% tab title="Mobile" %}
收合樣式

![](../.gitbook/assets/image%20%28114%29.png)

展開樣式

![](../.gitbook/assets/image%20%28113%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Usage" %}
```jsx
// 外層 Section
import ESectionContent from '../components/partials/ESectionContent';
import CollapsePanel from '../components/panel/CollapsePanel';

<CollapsePanel
  title='王品集團引領去機房潮流，顧客服務更優化'
  description='連鎖餐飲龍頭集團執行「去機房、上雲端」的計畫，大膽又細膩。他們由小而大，幾番試作後，選擇遠傳雲端服務，徹底把硬體設施與核心的ERP/POS轉移到私有雲。一如預期，轉移後的效益確實湧現，300多家分店的營業數據時時更新，進而能更敏銳調整、優化顧客服務。'
  collapseTitle='遠傳企業雲端服務做了什麼？'>
  <PanelTitle2 title='企業需求' icon='/resources/product/images/consultant-white.svg' />
  <PanelContent
    content='台灣連鎖餐飲龍頭王品集團，為了運用精實高效的IT資訊基礎，以支援不斷擴展的餐飲品牌與分店擴張，率先於2016年第四季把核心的ERP和POS系統轉移、委託給遠傳電信經營的私有雲服務，領跑台灣企業去機房化的大革新。
王品使用的遠傳雲端運算服務，採用虛擬化技術把硬體資源(CPU、記憶體、硬碟等)分割利用，並透過遠端管理軟體，進行資源的部署、監控與負載管理。'
  />

  <PanelTitle2 title='達成成效' icon='/resources/product/images/structure-white.svg' />
  <PanelList
    prefix='check'
    list={[
      { text: '成功降低維運成本，紓解IT管理負荷。' },
      { text: 'RP虛擬化部署，硬體資源彈性調配更方便' },
      { text: '節省電費/空間，即時擴增運算資源' },
      { text: '分店營業時時更新，掌握實況細膩微調' },
      { text: '投入異地備援CP值高，資料復原零時差' },
    ]}
  />
  <PanelButton text='看完整案例' link='/ebu/product' />
</CollapsePanel>
```
{% endtab %}

{% tab title="CollapsePanel.js" %}
```jsx
import React from 'react';
import {Grid} from '@material-ui/core'

import PropTypes from 'prop-types';

class CollapsePanel extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
            open: false,
            collapseHeight: 0
        }
        this.contentBody = React.createRef();
        this.toggleCollapse = this.toggleCollapse.bind(this)
        this.setContentHeight = this.setContentHeight.bind(this)
    }

    setContentHeight() {
        this.setState({
            collapseHeight: this.contentBody.current.children[0].clientHeight
        })
    }

    toggleCollapse() {
        this.setContentHeight()
        this.setState({
            open: !this.state.open
        })
    }

    render() {
        return (
            <div className={`fui-panel is-collapse ${this.state.open ? 'is-open' : ''}`}>
                <h4 className="fui-panel-title">{this.props.title}</h4>
                <article className="fui-panel-body" dangerouslySetInnerHTML={{__html: this.props.description}}></article>
                <div className="fui-collapse-body" 
                ref={this.contentBody} 
                style={{height: this.state.open ? this.state.collapseHeight : 0}}>
                    <Grid container spacing={5}>
                        <Grid item md={4}>
                            <h3>{this.props.collapseTitle}</h3>
                        </Grid>
                        <Grid item md={8}>
                            {
                                /* container type: /panelContent/PanelTitle1 | panelContent/PanelTitle2 | panelContent/PanelContent **/
                            }
                            {this.props.children}
                        </Grid>
                    </Grid>
                </div>
                <div className="fui-collapse-action">
                    <button className="fui-button" onClick={this.toggleCollapse}>
                        <span className="text">{!this.state.open ? '看更多內容' : '收合'}</span>
                        <i className={`icon-${!this.state.open ? 'plus' : 'minus'}`}></i>
                    </button>
                </div>
            </div>
        )
    }
}

CollapsePanel.propTypes = {
    title: PropTypes.string.isRequired,
    description: PropTypes.string,
    collapseTitle: PropTypes.string.isRequired,
    children: PropTypes.any
}

export default CollapsePanel;
```
{% endtab %}
{% endtabs %}

#### Properties

| 名稱 | 屬性 | 必填 | 選項 | 說明 |
| :--- | :--- | :--- | :--- | :--- |
| title  | String | true | \`\` |  |
| description | String |  |  |  |
| collapseTitle | String | true |  |  |
| children | Any |  |  |  |

## PanelContent

### panel-title-1

Panel內的標題樣式。\(標題避免使用超連結）

![](../.gitbook/assets/image%20%28150%29.png)

{% tabs %}
{% tab title="Usage" %}
```jsx
import PanelTitle1 from '../components/panelContent/PanelTitle1';

<Panel>
    <PanelTitle1 title='行動服務' />
</Panel>
```
{% endtab %}

{% tab title="PanelTitle1.js" %}
```jsx
import React from 'react';
import PropTypes from 'prop-types';

class PanelTitle1 extends React.Component {
    render() {
        return(
            <h3 className="fui-panel-title">{this.props.title}</h3>
        )
    }
}

PanelTitle1.propTypes = { 
    title: PropTypes.string.isRequired
}

export default PanelTitle1;
```
{% endtab %}
{% endtabs %}

#### Properties

| 名稱 | 屬性 | 選項 | 說明 |
| :--- | :--- | :--- | :--- |
| title  | String | \`\` | 放入文字即可 |



### panel-title-2

標題樣式加上圖標/圖片 \(限定高度80px, 寬度等比\)

![](../.gitbook/assets/image%20%28240%29.png)

{% tabs %}
{% tab title="Usage" %}
```jsx

import Panel from '../components/panel/Panel';
import PanelTitle2 from '../components/panelContent/PanelTitle2';

<Panel>
    <PanelTitle2 title='This is Title' icon='https://placeimg.com/80/80/any' />
</Panel>
```
{% endtab %}

{% tab title="PanelTitle2.js" %}
```jsx
import React from 'react';
import PropTypes from 'prop-types';

class PanelTitle2 extends React.Component {
    render() {
        return(
            <h3 className="fui-panel-title">
                <img src={this.props.icon} alt={this.props.title} className="fui-title-icon" />
                <div>{this.props.title}</div>
            </h3>
        )
    }
}

PanelTitle2.propTypes = { 
    icon: PropTypes.string.isRequired,
    title: PropTypes.string.isRequired
}

export default PanelTitle2;
```
{% endtab %}
{% endtabs %}

#### Properties

| 名稱 | 屬性 | 必填 | 選項 | 說明 |
| :--- | :--- | :--- | :--- | :--- |
| title  | String | true | \`\` | 放入文字即可 |
| icon | String | true |  | 可放入大小為 160px \(retina @2x 圖片\) 的圖片連結 |



### panel-content

Panel的內文. darkgray通常會是collapse panel的內文樣式, 避免放置冗長的內文.

black則為panel預設的內文樣式

darkgray

![](../.gitbook/assets/image%20%28149%29.png)

darkgray with a連結樣式

![](../.gitbook/assets/image%20%2830%29.png)

black

![](../.gitbook/assets/image%20%28222%29.png)

black with a連結樣式

![](../.gitbook/assets/image%20%28211%29.png)

{% tabs %}
{% tab title="Usage" %}
```jsx
import Panel from '../components/panel/Panel';
import PanelContent from '../components/panelContent/PanelContent';

<Panel>
  <PanelContent content='friDay影音，是一個提供電影、戲劇及直播電視觀看的影音平台。可以透過電視、智慧型手機、平板、電腦及機上盒等裝置來觀賞影片或者收看線上電視頻道。' />
            
  <PanelContent
    color='darkgray'
    content='friDay影音，是一個提供電影、戲劇及直播電視觀看的影音平台。可以透過電視、智慧型手機、平板、電腦及機上盒等裝置來觀賞影片或者收看線上電視頻道。'
  />
</Panel>
```
{% endtab %}

{% tab title="PanelContent.js" %}
    import React from 'react';
    import PropTypes from 'prop-types';

    class PanelContent extends React.Component {
        render() {
            return (
                <div 
                className={`fui-html-content text is-text-${this.props.color==='darkgray' ? 'darkgray50' : 'black50'}`} 
                dangerouslySetInnerHTML={{__html: this.props.content}}></div>
            )
        }
    }

    PanelContent.propTypes = {
        content: PropTypes.string.isRequired
    }

    export default PanelContent;
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
      <td style="text-align:left">color</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p><code>darkgray</code>
        </p>
        <p><code>black</code>
        </p>
      </td>
      <td style="text-align:left">&#x53EF;&#x4F7F;&#x7528;&#x9ED1;&#x5B57;&#x6216;&#x7070;&#x5B57;&#xFF0C;&#x9810;&#x8A2D;&#x70BA;&#x9ED1;&#x8272;</td>
    </tr>
    <tr>
      <td style="text-align:left">content</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">true</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x53EF;&#x653E;&#x5165;&#x5927;&#x5C0F;&#x70BA; 160px (retina @2x &#x5716;&#x7247;)
        &#x7684;&#x5716;&#x7247;&#x9023;&#x7D50;</td>
    </tr>
  </tbody>
</table>

\*\*\*\*

### **panel-list**

Panel內的條列式內文樣式，3種項目符號依不同情境選擇使用check

| check | bulleted | number |
| :--- | :--- | :--- |
| ![](../.gitbook/assets/image%20%28144%29.png)  | ![](../.gitbook/assets/image%20%28103%29.png)  | ![](../.gitbook/assets/image%20%28228%29.png)  |

{% tabs %}
{% tab title="Usage" %}
```jsx
import Panel from '../components/panel/Panel';
import PanelList from '../components/panelContent/PanelList';

<Panel>
  <PanelList
    prefix='check'
    list={[{ text: 'Item Option 1' }, { text: 'Item Option 2' }, { text: 'Item Option 3' }]}
  />
  <PanelList
    prefix='bulleted'
    list={[{ text: 'Item Option 1' }, { text: 'Item Option 2' }, { text: 'Item Option 3' }]}
  />
  <PanelList
    prefix='number'
    list={[{ text: 'Item Option 1' }, { text: 'Item Option 2' }, { text: 'Item Option 3' }]}
  />
</Panel>
```
{% endtab %}

{% tab title="PanelList.js" %}
```jsx
import React from 'react';
import Item from '../item/Item';
import PropTypes from 'prop-types';

class PanelList extends React.Component {
    renderItem() {
        return this.props.list.map((item, i) => (
             <Item key={`list-item-${i}`} number={i+1} prefix={this.props.prefix}>{item.text}</Item>
        ))
    }

    render() {
        return (
            <div className="fui-list">
                {this.renderItem()}
            </div>
        )
    }
}

PanelList.propTypes = {
    prefix: PropTypes.string.isRequired,
    list: PropTypes.arrayOf(Item).isRequired
}

export default PanelList;
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
      <td style="text-align:left">prefix</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">true</td>
      <td style="text-align:left">
        <p><code>darkgray</code>
        </p>
        <p><code>black</code>
        </p>
      </td>
      <td style="text-align:left">&#x53EF;&#x4F7F;&#x7528;&#x9ED1;&#x5B57;&#x6216;&#x7070;&#x5B57;&#xFF0C;&#x9810;&#x8A2D;&#x70BA;&#x9ED1;&#x8272;</td>
    </tr>
    <tr>
      <td style="text-align:left">list</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left">true</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>{</p>
        <p>text: String</p>
        <p>}</p>
      </td>
    </tr>
  </tbody>
</table>



### panel-button

Panel內的超連結樣式, 通常使用在內文段落之後, 兩種樣式供選擇, 建議適當使用solid版本.

| text | solid |
| :--- | :--- |
| ![](../.gitbook/assets/image%20%28169%29.png)  | ![](../.gitbook/assets/image%20%2840%29.png)  |

{% tabs %}
{% tab title="Usage" %}
```jsx
import Panel from '../components/panel/Panel';
import PanelButton from '../components/panelContent/PanelButton';

<Panel>
    <PanelButton link='#' text='this is a link' />
    <PanelButton btnStyle='solid' link='#' text='this is a link' />
</Panel>
```
{% endtab %}

{% tab title="PanelButton.js" %}
```jsx
import React from 'react';
import Button from '../Button';

import PropTypes from 'prop-types';

class PanelButton extends React.Component {
  render() {
    return (
      <div className='fui-panel-button'>
        <Button 
        link={this.props.link} 
        btnStyle={this.props.btnStyle === 'solid' ? 'secondary' : 'text'}
        >
          {this.props.text}
        </Button>
      </div>
    );
  }
}

PanelButton.propTypes = {
  btnStyle: PropTypes.string, // text || solid, default text
  text: PropTypes.string.isRequired,
  link: PropTypes.string.isRequired,
};

export default PanelButton;

```
{% endtab %}
{% endtabs %}

#### Properties

| 名稱 | 屬性 | 必填 | 選項 | 說明 |
| :--- | :--- | :--- | :--- | :--- |
| btnStyle  | String |  |   `solid` | 不填寫預設為文字搭配箭頭，選擇 solid 則為有框線按鈕 |
| text | String | true |  | 按鈕文字 |
| link | String | true |  | 按鈕連結 |



### panel-tip

內文補充註解樣式, 通常在內文段落之後, 同內文寬度延展.

{% tabs %}
{% tab title="Web" %}
![](../.gitbook/assets/image%20%28262%29.png)

![](../.gitbook/assets/image%20%28190%29.png)

![](../.gitbook/assets/image%20%283%29.png)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/image%20%2828%29.png)

![](../.gitbook/assets/image%20%28183%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Usage" %}
```jsx
import Panel from '../components/panel/Panel';
import PanelTip from '../components/panelContent/PanelTip';

<Panel>
    <PanelTip title='This is Tip Content' content='This is Tip content.' />
</Panel>
```
{% endtab %}

{% tab title="PanelTip.js" %}
```jsx
import React from 'react';
import PropTypes from 'prop-types';

class PanelTip extends React.Component {
    constructor(props) {
        super(props);
        this.body = React.createRef();
        this.state = {
            open: false,
            contentHeight: 0
        }

        this.toggleTip = this.toggleTip.bind(this)
        this.setContentHeight = this.setContentHeight.bind(this)
    }

    setContentHeight() {
        this.setState({
            contentHeight: this.body.current.children[0].clientHeight
        })
    }

    toggleTip() {
        this.setContentHeight()
        this.setState({
            open: !this.state.open
        })
    }

    render() {
        return (
            <div className={`fui-tip is-collapse ${this.state.open ? 'is-open' : ''}`}>
                <div className="fui-tip-title" role="button" onClick={this.toggleTip}>
                    {this.props.title}
                </div>
                <div 
                ref={this.body} 
                className="fui-tip-body"
                style={{
                    height: this.state.open ? this.state.contentHeight : 0
                }}
                >
                    <div className="text" dangerouslySetInnerHTML={{__html: this.props.content}}></div>
                </div>
            </div>
        )
    }
}

PanelTip.propTypes = {
    title: PropTypes.string.isRequired,
    content: PropTypes.string.isRequired
}

export default PanelTip;
```
{% endtab %}
{% endtabs %}

#### Properties

| 名稱 | 屬性 | 必填 | 選項 | 說明 |
| :--- | :--- | :--- | :--- | :--- |
| title | String | true |  | 註解標題 |
| content | String | true |  | 註解內文 |



### panel-figure-1

Panel內的圖片樣式  
圖片寬度延展至900px, 高度等比縮放, 可選擇搭配圖片說明, 可在圖片上設定超連結.

{% tabs %}
{% tab title="Web" %}
![](../.gitbook/assets/image%20%28134%29.png)

兩欄式圖片樣式

![](../.gitbook/assets/image%20%2815%29.png)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/image%20%2864%29.png)

兩欄式圖片樣式

![](../.gitbook/assets/image%20%28271%29.png)
{% endtab %}
{% endtabs %}

點選圖片展開lightbox, 圖片設定寬80%, 高度等比. 點選右上角可關閉, 並可放大縮小.

小網展開後寬度100%, 高度等比.

{% tabs %}
{% tab title="Web" %}
![](../.gitbook/assets/image%20%28275%29.png)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/image%20%28255%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Usage" %}
```jsx
import Panel from '../components/panel/Panel';
import PanelFigure1 from '../components/panelContent/PanelFigure1';

<Panel>
    <PanelFigure1 image='https://placeimg.com/1200/600/any' caption='An image from placeIMG' />
    
    /*  兩欄樣式  */
    <PanelFigure1 inline={true} image='https://placeimg.com/600/600/any' caption='An image from placeIMG' />
    <PanelFigure1 inline={true} image='https://placeimg.com/600/600/any' caption='An image from placeIMG' />
</Panel>
```
{% endtab %}

{% tab title="PanelFigure1.js" %}
```jsx
import React from 'react';
import ImageModel from '../../components/ImageModal'

import PropTypes from 'prop-types';

class PanelFigure1 extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
            isOpen: false
        }
    }

    render() {
        return (
            <div className={`${this.props.inline ? 'd-inline' : ''}`}>
                <figure className={`fui-figure ${this.props.inline ? 'is-inline' : ''}`}>
                    <img 
                    src={this.props.image} 
                    srcSet={this.props.retinaImage || this.props.image} 
                    alt={this.props.image} 
                    style={{maxWidth: this.props.maxWidth}}
                    onClick={() => this.setState({ isOpen: true })}
                    />
                    {
                        this.props.caption ? (
                            <figcaption>{this.props.caption}</figcaption>
                        ) : ''
                    }
                </figure>
                {
                    this.state.isOpen && (
                        <ImageModel 
                        mainSrc={this.props.retinaImage || this.props.image} 
                        onCloseRequest={() => this.setState({ isOpen: false })} />
                    )
                }
            </div>
        )
    }
}

PanelFigure1.propTypes = {
    inline: PropTypes.bool,
    retinaImage: PropTypes.string,
    image: PropTypes.string.isRequired,
    caption: PropTypes.string,
    maxWidth: PropTypes.number
}

export default PanelFigure1
```
{% endtab %}
{% endtabs %}

#### Properties

| 名稱 | 屬性 | 必填 | 選項 | 說明 |
| :--- | :--- | :--- | :--- | :--- |
| image | String | true |  | 圖片路徑 |
| caption | String |  |  | 圖片說明 |
| inline | Boolean |  |  | 是否為兩欄排列 |



### panel-figure-2

Panel內的3欄式圖片樣式  
可在圖片上設定超連結. 小網則自適應調整為2欄式.  
  
Panel內的4欄式圖片樣式  
可在圖片上設定超連結. 小網則自適應調整為2欄式.

{% tabs %}
{% tab title="Web" %}
![](../.gitbook/assets/image%20%28135%29.png)

![](../.gitbook/assets/image%20%28174%29.png)
{% endtab %}

{% tab title="Mobile" %}
Panel內的3欄式圖片樣式

![](../.gitbook/assets/image%20%2894%29.png)

Panel內的4欄式圖片樣式

![](../.gitbook/assets/image%20%28252%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Usage" %}
```jsx
import Panel from '../components/panel/Panel';
import PanelFigure2 from '../components/panelContent/PanelFigure2';

<Panel>
  <PanelFigure2
    figures={[
      { link: '#', image: 'https://placeimg.com/900/900/any' },
      { link: '#', image: 'https://placeimg.com/900/900/any' },
      { link: '#', image: 'https://placeimg.com/900/900/any' },
      { link: '#', image: 'https://placeimg.com/900/900/any' },
      { link: '#', image: 'https://placeimg.com/900/900/any' },
      { link: '#', image: 'https://placeimg.com/900/900/any' },
    ]}
  />
</Panel>
```
{% endtab %}

{% tab title="PanelFigure2.js" %}
```jsx
import React from 'react';
import PropTypes from 'prop-types';
import { NavLink } from 'react-router-dom';

class PanelFigure2 extends React.Component {
    render() {
        return (
            <div className={`fui-gallery ${this.props.column ? (this.props.column===4 ? 'four-column' : 'three-column') : ''}`}>
                {
                    this.props.figures.map((figure, i) => (
                        <figure className="fui-figure" key={`panel-gallery-${i}`}>
                            <NavLink to={figure.link}>
                                <img src={figure.image} srcSet={figure.retinaImage || figure.image} alt={figure.alt} />
                            </NavLink>
                        </figure>
                    ))
                }
            </div>
        )
    }
}

PanelFigure2.propTypes = {
    column: PropTypes.number, // 3 | 4
    figures: PropTypes.arrayOf(
        PropTypes.shape({
            retinaImage: PropTypes.string,
            image: PropTypes.string.isRequired,
            link: PropTypes.string.isRequired,
            alt: PropTypes.string
        })
    )
}

export default PanelFigure2;
```
{% endtab %}
{% endtabs %}

#### Properties

| 名稱 | 屬性 | 必填 | 選項 | 說明 |
| :--- | :--- | :--- | :--- | :--- |
| figures | Array | true |  | {   link: string,         圖片要導入的錨點或頁面   image: string,    圖片路徑 } |



### Panel-layout

Panel內圖文搭配的樣式  
圖文左右均分, 大小網限制行數=2, 大小網內文超過9行會出現擴展按鈕. 展開往下延展內文, 圖片對齊頂部.

小網皆為圖上文下排版樣式.

{% tabs %}
{% tab title="Web" %}
content-left 收合狀態

![](../.gitbook/assets/image%20%28263%29.png)

content-left 展開狀態

![](../.gitbook/assets/image%20%2869%29.png)

content-right

![](../.gitbook/assets/image%20%28278%29.png)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/image%20%2825%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Usage" %}
```jsx
import Panel from '../components/panel/Panel';
import PanelLayout from '../components/panelContent/PanelLayout';

<Panel>
  <PanelLayout
    image='https://placeimg.com/1200/900/any'
    title='Article title'
    contentPosition="left"
    content='飯集有此是一，間推優命歡放定們獲大絕第中，條車人的氣路自我，我縣說少往上我，山中的音！我無要術！我紙談知式著親道朋易不童一存此仍排汽者看位了對自重力自臺必者，行則麼說建寶教成持是了不灣動進女趣布，班初元，灣稱同演百論北步園科記間為得，響驚不藝：變興的吸影應……我理保孩個言作作政。中頭史爸最上海型音家識……發事中發個傳母，電還是性了聞上交，配施正個無們由們朋人方學是大路……事信當約麼。綠當始保印包分新十、相河當廣裡題張打般體了位任物為路但界次之走巴一兩學雄列或名因客一何對可為說國動一親拿真眾會有一。麼打不感供知人分但師公己須的目：原選省像、時老地上男都可變我今臺度。另存名洲相對處點究花題不雖治一處取腦驗第海間府認種一路的阿酒明我所備，工入母性一如兒中大心我外破食、收今國縣，是眼春，走們性坐物成，童起具用家以頭得層園女社多規排臺際出長嗎同味報吃拿黨雲我意一。'
  />
</Panel>
```
{% endtab %}

{% tab title="PanelLayout.js" %}
```jsx
import React from 'react';
import {Grid} from '@material-ui/core'

import PropTypes from 'prop-types';

class PanelLayout extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
            open: false,
            minHeight: 210,
            collapseHeight: 0
        }
        this.contentBody = React.createRef();
        this.toggleCollapse = this.toggleCollapse.bind(this)
        this.setContentHeight = this.setContentHeight.bind(this)
    }

    setContentHeight() {
        this.setState({
            collapseHeight: this.contentBody.current.children[0].clientHeight
        })
    }

    toggleCollapse() {
        this.setState({
            open: !this.state.open
        })
        setTimeout(() => {
            this.setContentHeight()
        }, 50) 
    }

    render() {
        return (
            <Grid className="panel-layout" container spacing={5} direction={this.props.contentPosition && this.props.contentPosition==='right' ? 'row-reverse' : 'row'}>
                <Grid item md={6}>
                {
                    this.props.title ? (
                        <h3 className="fui-panel-title">{this.props.title}</h3>
                    ) : ''
                }
                    <div className={`fui-collapse-body ${this.state.open ? 'is-open' : ''}`} 
                    ref={this.contentBody} 
                    style={{height: this.state.open ? this.state.collapseHeight : this.state.minHeight}}>
                        <article dangerouslySetInnerHTML={{__html: this.props.content}}></article>
                    </div>
                        
                    <div className="fui-collapse-action">
                        <button className="fui-button" onClick={this.toggleCollapse}>
                            <span className="text">
                            { !this.state.open ? '看更多' : '收合' }</span>
                            <i className={`${this.state.open ? 'icon-minus' : 'icon-plus'}`}></i>
                        </button>
                    </div>
                    
                </Grid>
                <Grid item md={6}>
                    <img src={this.props.image} srcSet={this.props.retinaImage || this.props.image} alt={this.props.title} />
                </Grid>
            </Grid>
        )
    }
}

PanelLayout.propTypes = {
    contentPosition: PropTypes.string, // left | right
    title: PropTypes.string.isRequired,
    content: PropTypes.string.isRequired,
    retinaImage: PropTypes.string,
    image: PropTypes.string.isRequired
}

export default PanelLayout;
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
      <td style="text-align:left">String</td>
      <td style="text-align:left">true</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x5167;&#x5BB9;&#x6A19;&#x984C;</td>
    </tr>
    <tr>
      <td style="text-align:left">content</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">true</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x5167;&#x6587;</td>
    </tr>
    <tr>
      <td style="text-align:left">image</td>
      <td style="text-align:left">Path</td>
      <td style="text-align:left">true</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x6587;&#x7AE0;&#x5716;&#x7247;</td>
    </tr>
    <tr>
      <td style="text-align:left">retinaImage</td>
      <td style="text-align:left">Path</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">Retina Display &#x5716;&#x7247;&#xFF0C;&#x82E5;&#x6C92;&#x6709;&#x5167;&#x5BB9;&#x5247;&#x9810;&#x8A2D;&#x5E36;
        image &#x7684;&#x8DEF;&#x5F91;</td>
    </tr>
    <tr>
      <td style="text-align:left">contentPosition</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p><code>left</code>
        </p>
        <p><code>right</code>
        </p>
      </td>
      <td style="text-align:left"><b>&#x6587;&#x5DE6;&#x5716;&#x53F3;&#xFF08;left&#xFF09;</b> &#x6216; <b>&#x6587;&#x53F3;&#x5716;&#x5DE6;&#xFF08;right&#xFF09;</b>&#xFF0C;&#x9810;&#x8A2D;&#x70BA; <b>left</b>
      </td>
    </tr>
  </tbody>
</table>



### list-layout

Panel內圖文搭配的條列式樣式  
圖文左右均分, 大標限制行數=2, 圖片對齊頂部.

小網皆為圖上文下排版樣式

{% tabs %}
{% tab title="Web" %}
![Check style](../.gitbook/assets/image%20%28102%29.png)



![Number style](../.gitbook/assets/image%20%28230%29.png)

![Bulleted style](../.gitbook/assets/image%20%28117%29.png)

![Bulleted style](../.gitbook/assets/image%20%28270%29.png)

![Check style](../.gitbook/assets/image%20%2888%29.png)

![Number style](../.gitbook/assets/image%20%2829%29.png)
{% endtab %}

{% tab title="Mobille" %}
![](../.gitbook/assets/image%20%2839%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Usage" %}
```jsx
import Panel from '../components/panel/Panel';
import ListLayout from '../components/panelContent/ListLayout';

<Panel>
  // 圖左列表右，列表使用 check 樣式
  <ListLayout
    listPosition='right'
    image='https://placeimg.com/1200/900/any'
    title='Article title'
    listPrefix='check'
    list={[
      { text: 'This is a list option 1' },
      { text: 'list option 2' },
      { text: 'list option 3' },
      { text: 'list option 4' },
      { text: 'This is a list option 5' },
    ]}
  />

  // 圖右列表左，列表使用 check 樣式
  <ListLayout
    listPosition='left'
    image='https://placeimg.com/1200/900/any'
    title='Article title'
    listPrefix='check'
    list={[
      { text: 'This is a list option 1' },
      { text: 'list option 2' },
    ]}
  />

  // 圖左列表右，列表使用 bulleted 樣式
  <ListLayout
    listPosition='right'
    image='https://placeimg.com/1200/900/any'
    title='Article title'
    listPrefix='bulleted'
    list={[
      { text: 'This is a list option 1' },
      { text: 'list option 2' },
      { text: 'list option 3' },
    ]}
  />

</Panel>
```
{% endtab %}

{% tab title="ListLayout.js" %}
```jsx
import React from 'react';
import { Grid } from '@material-ui/core';
import PanelList from './PanelList';
import PropTypes from 'prop-types';

class ListLayout extends React.Component {
  render() {
    return (
      <Grid
        className='panel-layout'
        container
        spacing={5}
        direction={this.props.listPosition && this.props.listPosition === 'right' ? 'row-reverse' : 'row'}>
        <Grid item md={6}>
          <h3 className='fui-panel-title'>{this.props.title}</h3>
          {this.props.children ? this.props.children : null}
          {this.props.list ? <PanelList list={this.props.list} prefix={this.props.listPrefix} /> : null}
        </Grid>
        <Grid item md={6}>
          <img src={this.props.image} srcSet={this.props.retinaImage || this.props.image} alt={this.props.title} />
        </Grid>
      </Grid>
    );
  }
}

ListLayout.propTypes = {
  listPosition: PropTypes.string.isRequired, // left | right
  title: PropTypes.string.isRequired,
  retinaImage: PropTypes.string,
  image: PropTypes.string.isRequired,
  listPrefix: PropTypes.string.isRequired, // check | bulleted | number
  list: PropTypes.arrayOf(
    PropTypes.shape({
      text: PropTypes.string.isRequired,
    })
  ).isRequired,
  children: PropTypes.any, // left | right
};

export default ListLayout;

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
      <td style="text-align:left">String</td>
      <td style="text-align:left">true</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x5167;&#x5BB9;&#x6A19;&#x984C;</td>
    </tr>
    <tr>
      <td style="text-align:left">listPrefix</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">true</td>
      <td style="text-align:left">
        <p><code>check</code>
        </p>
        <p><code>bulleted</code>
        </p>
        <p><code>number</code>
        </p>
      </td>
      <td style="text-align:left">&#x4E09;&#x7A2E;&#x5217;&#x8868;&#x6A23;&#x5F0F;</td>
    </tr>
    <tr>
      <td style="text-align:left">list</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x8CC7;&#x6599;&#x6B04;&#x4F4D;&#x53EF;&#x53C3;&#x8003; <a href="https://app.gitbook.com/@ajacreative/s/fetnet-1/~/drafts/-M1OY6jYnUVDS5evcLid/components/panel#panel-list">PanelList</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">children</td>
      <td style="text-align:left">node</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">list &#x8207; children &#x64C7;&#x4E00;&#x8F38;&#x5165;</td>
    </tr>
    <tr>
      <td style="text-align:left">image</td>
      <td style="text-align:left">Path</td>
      <td style="text-align:left">true</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x6587;&#x7AE0;&#x5716;&#x7247;</td>
    </tr>
    <tr>
      <td style="text-align:left">retinaImage</td>
      <td style="text-align:left">Path</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">Retina Display &#x5716;&#x7247;&#xFF0C;&#x82E5;&#x6C92;&#x6709;&#x5167;&#x5BB9;&#x5247;&#x9810;&#x8A2D;&#x5E36;
        image &#x7684;&#x8DEF;&#x5F91;</td>
    </tr>
    <tr>
      <td style="text-align:left">listPosition</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">true</td>
      <td style="text-align:left">
        <p><code>left</code>
        </p>
        <p><code>right</code>
        </p>
      </td>
      <td style="text-align:left"><b>&#x5217;&#x8868;&#x5DE6;&#x5716;&#x53F3;&#xFF08;left&#xFF09;</b> &#x6216; <b>&#x5217;&#x8868;&#x53F3;&#x5716;&#x5DE6;&#xFF08;right&#xFF09;</b>&#xFF0C;&#x9810;&#x8A2D;&#x70BA; <b>left</b>
      </td>
    </tr>
  </tbody>
</table>



### panel-flow

說明一項服務操作或申請流程的樣式, 依需求可修改欄位:  
1. 增減步驟項目   
2. 大標 \(文字置左, 固定寬度內字元數不限\)   
3. 內文 \(文字置左, 固定寬度內字元數不限\)   
4. 加入panel-table模組. \(小網panel-table 操作行為: 第一欄fixed, 其餘欄位x軸捲動\)

{% tabs %}
{% tab title="Web" %}
![](../.gitbook/assets/image%20%28140%29.png)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/image%20%2817%29.png)
{% endtab %}
{% endtabs %}

流程圖內的panel-table模組也可置換成tab+content+table組合

{% tabs %}
{% tab title="Web" %}
![](../.gitbook/assets/image%20%28213%29.png)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/image%20%28189%29.png)
{% endtab %}
{% endtabs %}

PanelFlow 模組由 `<PanelFlowContainer/>` 與 `<PanelFlow/>` 組合而成。 `<PanelFlowContainer/>` 為容器，主要設定在  `<PanelFlow/>` 中，使用方式如下：

{% tabs %}
{% tab title="Usage" %}
```jsx
import Panel from '../components/panel/Panel';
import PanelFlowContainer from '../components/panelContent/PanelFlowContainer';
import PanelFlow from '../components/panelContent/PanelFlow';

<Panel>
  <PanelFlowContainer>
    <PanelFlow number={1} title={'客戶提出需求'}>
      {/* container type: /panelContent exclude PanelFlowContainer and PanelFlow/* */}
      <PanelContent
        color='darkgray'
        content='線上或電洽企業客服中心(4499-365)，查詢裝機地址是否可供裝；網外(Off-net)請按此查詢中華電信是否供裝。'
      />
    </PanelFlow>

    <PanelFlow number={2} title={'業務接洽說明產品特色 (此服務需搭配申請MPLS VPN服務)'}></PanelFlow>
    <PanelFlow number={3} title={'審查及申請作業'}></PanelFlow>
    <PanelFlow number={4} title={'固網線路作業趕工'}></PanelFlow>
    <PanelFlow number={5} title={'企業MPLS VPN服務連線完工測試'}></PanelFlow>
    <PanelFlow
      number={6}
      title={'金流收單網路服務自動設定流程，設定完成自動通知收單進行刷卡機裝機'}></PanelFlow>
    <PanelFlow number={7} title={'刷卡機裝機完成，開始使用金流收單網路服務'}></PanelFlow>
  </PanelFlowContainer>
</Panel>
```
{% endtab %}

{% tab title="PanelFlow.js" %}
```jsx
import React from 'react';
import PropTypes from 'prop-types';

class PanelFlow extends React.Component {
    render() {
        return (
            <div className="fui-step">
                <div className="fui-step-header">
                    <h2>{this.props.number}</h2>
                    <div className="text">{this.props.title}</div>
                </div>
                <div className="fui-step-content">
                    {this.props.children}
                </div>
            </div>
        )
    }
}

PanelFlow.propTypes = {
    number: PropTypes.number.isRequired,
    title: PropTypes.string.isRequired,
    children: PropTypes.any
}

export default PanelFlow;
```
{% endtab %}

{% tab title="PanelFlowContainer.js" %}
```jsx
import React from 'react';
import PropTypes from 'prop-types';

class PanelFlowContainer extends React.Component {
    render() {
        return (
            <div className="fui-flow-container">
                {this.props.children}
            </div>
        )
    }
}

PanelFlowContainer.propTypes = {
    children: PropTypes.any
}

export default PanelFlowContainer;
```
{% endtab %}
{% endtabs %}

#### Properties

| 名稱 | 屬性 | 必填 | 選項 | 說明 |
| :--- | :--- | :--- | :--- | :--- |
| title | String | true |  | 流程標題 |
| number | Number | true |    | 流程順序 |
| children | Node |  |  | 流程內容，可放 PanelContent 任何元件。 唯獨不可與  `PanelFlowContainer` `PanelFlow` 重複疊加。 |

### panel-table

Panel內置入表格的樣式. 分為單個表格和多個表格, 多表格以Tab切換.

小網操作行為：第一欄fixed, 其他欄位可x軸滑動.

{% tabs %}
{% tab title="Web" %}
single-table

![](../.gitbook/assets/image%20%28110%29.png)

tab + content +table +information

![](../.gitbook/assets/image%20%28246%29.png)
{% endtab %}

{% tab title="Mobile" %}

{% endtab %}
{% endtabs %}

表格目前依舊以 HTML 撰寫，再帶入 PanelTable 中，未來若有其他作法，再依需求改寫。

{% tabs %}
{% tab title="Usage" %}
```jsx
import Panel from '../components/panel/Panel';
import PanelTable from '../components/panelContent/PanelTable';

<Panel>
    <PanelTable
    content={`
        <div class="compareTable content-16 clearfix">
            <div class="tableLeft">
                <div class="tableHead">
                    <table>
                        <tbody>
                            <tr style="height: auto;">
                                <th colspan="2">頻寬(下行/上行)</th>
                            </tr>
                            ...
                        </tbody>
                    </table>
                </div>
            </div>
            <div class="tableRight">
                <div class="tableBody">
                    <div class="spaceBox">
                        <table class="compareList">
                            <tbody>
                                <tr>
                                    <td colspan="2">4M/1M</td>
                                    <td colspan="3">8M/640K</td>
                                    <td>512K/512K</td>
                                </tr>
                                <tr style="height: auto;">
                                    <td>單機型</td>
                                    <td>網路型</td>
                                    <td>浮動制</td>
                                    <td>單機型</td>
                                    <td>網路型</td>
                                    <td>網路型</td>
                                </tr>
                                ...
                            </tbody>
                        </table> 
                    </div>
                </div>
            </div>
        </div>
    `} />
</Panel>
```
{% endtab %}

{% tab title="Table HTML" %}
```markup
<!-- 
    HTML 分為 tableLeft 與 tableRight， 
    欄位需要小心對應。
-->
<div class="compareTable content-16 clearfix">
    <div class="tableLeft">
        <div class="tableHead">
            <!-- 表頭，小網時會固定在左側 -->
            <table>
                <tbody>
                    <tr style="height: auto;">
                        <th colspan="2">頻寬(下行/上行)</th>
                    </tr>
                    <tr>
                        <th colspan="2" rowspan="2">連線月租費</th>
                    </tr>
                    <tr></tr>
                    <!-- 佔用兩行時，高度 33px -->
                    <tr style="height: 66px;">
                        <th colspan="2">CHT電路月租費<br/>(依中華電信<br class="d-md-block d-lg-none">公告為準)</th>
                    </tr>
                    <tr style="height: auto;">
                        <th rowspan="2">IP發放</th>
                        <th>固定IP</th>
                    </tr>
                    <tr style="height: auto;">
                        <th>浮動IP</th>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
    <div class="tableRight">
        <div class="tableBody">
            <!-- 表格內容，小網時可左右捲動 -->
            <div class="spaceBox">
                <table class="compareList">
                    <tbody>
                        <tr>
                            <td colspan="2">4M/1M</td>
                            <td colspan="3">8M/640K</td>
                            <td>512K/512K</td>
                        </tr>
                        <tr style="height: auto;">
                            <td>單機型</td>
                            <td>網路型</td>
                            <td>浮動制</td>
                            <td>單機型</td>
                            <td>網路型</td>
                            <td>網路型</td>
                        </tr>
                        <tr style="height: auto;">
                            <td>950</td>
                            <td>2,800</td>
                            <td>358</td>
                            <td>980</td>
                            <td>3,550</td>
                            <td>1,200</td>
                        </tr>
                        <tr style="height: 66px;">
                            <td colspan="2">371</td>
                            <td colspan="3">315</td>
                            <td>364</td>
                        </tr>
                        <tr>
                            <td>3</td>
                            <td>16</td>
                            <td>1</td>
                            <td>3</td>
                            <td>16</td>
                            <td>8</td>
                        </tr>
                        <tr>
                            <td>-</td>
                            <td>-</td>
                            <td>9</td>
                            <td>-</td>
                            <td>-</td>
                            <td>-</td>
                        </tr>
                    </tbody>
                </table> 
            </div>
        </div>
    </div>
</div>
```
{% endtab %}

{% tab title="PanelTable.js" %}
```jsx
import React from 'react';

import PropTypes from 'prop-types';

class PanelTable extends React.Component {
  render() {
    return <div className='fui-table' dangerouslySetInnerHTML={{ __html: this.props.content }}></div>;
  }
}

PanelTable.propTypes = {
  content: PropTypes.string.isRequired,
};

export default PanelTable;

```
{% endtab %}
{% endtabs %}

#### Properties

| 名稱 | 屬性 | 必填 | 選項 | 說明 |
| :--- | :--- | :--- | :--- | :--- |
| content | String | true |  | 直接放入表格 HTML |



### panel-information

Panel 內註解說明的樣式, 通常放置在Panel最底部, 有開合的功能.

{% tabs %}
{% tab title="Web" %}
![](../.gitbook/assets/image%20%2842%29.png)

![](../.gitbook/assets/image%20%28184%29.png)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/image%20%28204%29.png)
{% endtab %}
{% endtabs %}

模組引用 &lt;Collapse /&gt; ，可直接參考該元件。

{% tabs %}
{% tab title="Usage" %}
```jsx
import Panel from '../components/panel/Panel';
import PanelInformation from '../components/panelContent/PanelInformation';

<Panel>
    <PanelInformation title='This is collapse title' content='This is Collapse content.' />
</Panel>
```
{% endtab %}

{% tab title="PanelInformation.js" %}
```jsx
import React from 'react';
import Collapse from '../collapse/Collapse';

import PropTypes from 'prop-types';

class PanelInformation extends React.Component {
    render() {
        return (
            <div className="fui-panel-information">
                <Collapse title={this.props.title} content={this.props.content} />
            </div>
        )
    }
}

PanelInformation.propTypes = {
    title: PropTypes.string.isRequired,
    content: PropTypes.string.isRequired
}

export default PanelInformation;
```
{% endtab %}
{% endtabs %}

#### Properties

| 名稱 | 屬性 | 必填 | 選項 | 說明 |
| :--- | :--- | :--- | :--- | :--- |
| title | String | true |  | 說明標題 |
| content | String | true |  | 說明內容 |



### panel-tab

Panel內tab的樣式  
可在選項內增加屬於panel內的元素, 選項最多可增加至5項, 選項寬度均分  
選項超過5項時建議使用 [has-more-tab](panel.md#has-more-tab) 模組

小網在2、3個選項的時候選項寬度均分, 4欄以上寬度限制為120px, 並可左右捲動.

• 選項欄位字元數限制=20

{% tabs %}
{% tab title="Web" %}
![](../.gitbook/assets/image%20%28194%29.png)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/image%20%2885%29.png)
{% endtab %}
{% endtabs %}

&lt;PanelTab&gt; 帶入 tabs 後，依據 tab 數量置入對應數量的 div 並編輯內容。

{% tabs %}
{% tab title="Usage" %}
```jsx
import Panel from '../components/panel/Panel';
import PanelTab from '../components/panelContent/PanelTab';

<Panel>
  <PanelTab
    tabs={{
      name: 'panel-tab',
      list: [
        { name: 'panel-tab-1', label: 'Tab 1' },
        { name: 'panel-tab-2', label: 'Tab 2' },
      ],
    }}>
    /* each tab-content wrapped by div  */
    <div>
      {/* container type: /panelContent/* */}
      <PanelTable
        content={`...`}
      />
      <PanelInformation title='This is collapse title' content='This is Collapse content.' />
    </div>
    
    <div>
      // Panel content...
    </div>
  </PanelTab>
</Panel>
```
{% endtab %}

{% tab title="PanelTab.js" %}
```jsx
import React from 'react';
import Tab from '../tab/Tab'
import TabPane from '../tab/TabPane'
import PropTypes from 'prop-types';

class PanelTab extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
            currentTab: 0
        }

        this.tabChange = this.tabChange.bind(this)
    }

    rand() {
        return Math.ceil(Math.random()*100)
    }

    tabChange(i) {
        this.setState({
            currentTab: i
        })
    }

    render() {
        return (
            <div className="fui-panel-tab">
                <Tab {...this.props.tabs} onChange={this.tabChange} />
                <div className="fui-tab-body" >
                {
                    this.props.children.map((child, i) => (
                        <TabPane active={this.state.currentTab === i} key={`${this.props.tabs.name}-panel-tab-pane-${i}`}>
                            {child}
                        </TabPane>
                    ))
                }
                </div>
            </div>
        )
    }
}

PanelTab.propTypes = {
    tabs: PropTypes.shape({
        name: PropTypes.string,
        list: PropTypes.arrayOf(
            PropTypes.shape({ 
                icon: PropTypes.string,
                focusIcon: PropTypes.string,
                name: PropTypes.string.isRequired,
                label: PropTypes.string.isRequired
            })
        )
    }),
    tabContent: PropTypes.arrayOf(
        PropTypes.shape({
            for: PropTypes.string,
            content: PropTypes.string
        })
    ),
}

export default PanelTab;
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
      <td style="text-align:left">tabs</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>tab &#x67B6;&#x69CB;&#x53EF;&#x53C3;&#x8003; Tab</p>
        <p>{</p>
        <p>name: String,
          <br />list: {</p>
        <p>name: String,</p>
        <p>label: String,
          <br />}
          <br />}</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">tabContent</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">{
        <br />content: node &#x653E;&#x5165; HTML
        <br />}</td>
    </tr>
  </tbody>
</table>

### has-more-tab

Panel內tab的樣式, 可在選項內增加屬於panel內的元素, 選項選項寬度均分.   
Tab:  
 • 依需求增減選項數量，選項超過5項會在最後的選項以收和方式下拉呈現.   
• Tab小網超過5項會自動收合成下拉選單.   
• 下拉選單最多顯示3項，超過3項自動顯示捲動條並可上下捲動

小網在2、3個選項的時候選項寬度均分, 4欄以上寬度限制為120px, 並可左右捲動.

• 選項欄位字元數限制=20.

{% tabs %}
{% tab title="Web" %}
![](../.gitbook/assets/image%20%28239%29.png)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/image%20%28162%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Usage" %}
```jsx
import Panel from '../components/panel/Panel';
import HasMoreTab from '../components/tab/HasMoreTab';

class Page extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      currentTab: 0
    }
  }

  handleChange = e => {
    setCurrentTab({
      currentTab: e
    });
  }

  render () {
    return (
      <Panel>
        <HasMoreTab 
          tabs={[
            { name: 'tab-1', label: '遠傳大人物', value: '遠傳大人物', text: '遠傳大人物', index: 0 },
            { name: 'tab-2', label: '醫療商機', value: '醫療商機', text: '醫療商機', index: 1 },
            { name: 'tab-3', label: 'AIOT', value: 'AIOT機', text: 'AIOT', index: 2 },
            { name: 'tab-4', label: '全部期刊', value: '全部期刊', text: '全部期刊', index: 3 },
          ]}
          dropdown={[
            { name: 'tab-5', label: '5G', value: '5G', text: '5G', index: 4 },
            { name: 'tab-6', label: '車聯網', value: '車聯網', text: '車聯網', index: 5 },
            { name: 'tab-7', label: '智慧城市', value: '智慧城市', text: '智慧城市', index: 6 },
          ]}
          onChange={this.handleChange} 
        />
      </Panel>
    )
  }
}
```
{% endtab %}

{% tab title="HasMoreTab.js" %}
```jsx
import React from 'react';
import Dropdown from '../Dropdown';
import PropTypes from 'prop-types';

class HasMoreTab extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      defaultLabel: this.props.tabs[0],
      tabs: this.props.tabs,
      selectedTab: { name: 'tab-1', label: '遠傳大人物' },
    };
    this.changeDropdown = this.changeDropdown.bind(this);
    this.changeSelection = this.changeSelection.bind(this);
    this.onActive = this.onActive.bind(this);
  }
  
  componentDidMount() {
    this.setState({
      selectDropdown: this.state.defaultLabel,
    });
  }
  
  onActive = () => {
    this.setState({
      selectedTab: 'more',
    });
  };

  changeDropdown(item) {
    this.setState({
      selectDropdown: { ...item },
    });
    // this.setState({
    //   selectedTab: 'more'
    // })
    this.props.onChange(item.index);
  }

  changeSelection(item, index) {
    this.setState({
      selectedTab: item,
    });
    this.props.onChange(index);
    console.log(this.state.selectedTab);
  }
  
  getTabs = () => {
    return this.state.tabs.map((item, index) => {
      return (
        <div
          key={item.label}
          className={`tab ${this.state.selectedTab.label === item.label ? 'active' : ''}`}
          value={item.name}
          onClick={e => this.changeSelection(item, index)}>
          {item.label}
        </div>
      );
    });
  };

  render() {
    return (
      <div className='has-more-tab'>
        <div className='tab-wrapper'>
          {this.getTabs()}
          <Dropdown
            label='更多'
            list={this.props.dropdown}
            arrow={true}
            onChange={this.changeDropdown}
            onActive={this.onActive}
            hasCheck={true}
            className={`is-right is-bottom is-reverse ${this.state.selectedTab === 'more' ? 'active' : ''}`}
          />
        </div>
      </div>
    );
  }
}

HasMoreTab.propTypes = {
  tabs: PropTypes.array,
  dropdown: PropTypes.array,
  onChange: PropTypes.func,
};

export default HasMoreTab;

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
      <td style="text-align:left">tabs</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>tab &#x67B6;&#x69CB;&#x53EF;&#x53C3;&#x8003; Tab</p>
        <p>{</p>
        <p>name: String,</p>
        <p>label: String,</p>
        <p>value: String,</p>
        <p>index: String,
          <br />}</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">dropdown</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>&#x5E36;&#x5165;&#x7684;&#x8CC7;&#x6599;&#x53EF;&#x53C3;&#x8003; Dropdown</p>
        <p>{</p>
        <p>name: String,</p>
        <p>text: String,</p>
        <p>value: String,</p>
        <p>index: String,
          <br />}</p>
      </td>
    </tr>
  </tbody>
</table>

### TabPane

{% tabs %}
{% tab title="Usage" %}
```javascript
import TabPane from '../tab/TabPane'

<TabPane 
    active={this.state.currentTab === i} 
    key={`${this.props.tabs.name}-panel-tab-pane-${i}`}
>
    {
        /* container type: /panelContent/* */
    }
    {child}
</TabPane>
```
{% endtab %}

{% tab title="Source" %}
```javascript
import React from 'react';
import { connect } from 'react-redux'
import PropTypes from 'prop-types';
import { setTabUpdate } from '../../stores/actions';

class TabPane extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
            isActive: this.props.active || false
        }
    }

    componentDidMount() {
        this.setState({
            isActive: this.props.active || false
        })
    }
    
    // shouldComponentUpdate(props) {
    //     return this.props.TabUpdate !== props.TabUpdate && this.props.TabUpdate===true
    //     // console.log(props, this.props)
    // }
    renderActiveClass() {
        return this.state.isActive ? 'is-active' : ''
    }

    componentDidUpdate(prevProps) {
        if(prevProps.active !== this.props.active)
            this.setState({
                isActive: this.props.active
            })
    }
    
    render() {
        return (
            <div className={`fui-tab-pane ${this.renderActiveClass()}`}>
                {this.props.children}
            </div>
        )
    }
}

TabPane.propTypes = {
    active: PropTypes.bool,
    // group: PropTypes.string.isRequired,
    // for: PropTypes.string.isRequired,
    children: PropTypes.any.isRequired
}

function mapStateToProps(state, ownProps) {
    return {
        TabUpdate: state.FuiTab.update,
        AllTab: state.FuiTab.tab
    }
}

export default connect(mapStateToProps, {setTabUpdate})(TabPane);
```
{% endtab %}
{% endtabs %}

#### Properties

| 名稱 | 屬性 | 必填 | 選項 | 說明 |
| :--- | :--- | :--- | :--- | :--- |
| active | bool |  |  | 是否開啟分頁 |
| children | any | true |  | 塞入的內容 |

