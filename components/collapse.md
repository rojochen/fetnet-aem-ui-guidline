# Collapse

{% code title="Collapse.js" %}
```jsx
import React from 'react';
import PropTypes from 'prop-types';

class Collapse extends React.Component {
    constructor(props) {
        super(props);
        this.body = React.createRef();
        this.state = {
            contentHeight: 0,
            open: this.props.open || false
        }

        this.collapseOpen = this.collapseOpen.bind(this)
        this.setContentHeight = this.setContentHeight.bind(this)
    }

    setContentHeight() {
        this.setState({
            contentHeight: this.body.current.clientHeight
        })
    }

    componentDidUpdate(nextProps) {
        if(this.props.onChange && (nextProps.open !== this.state.open || this.props.open !==this.state.open)) {
            this.setState({
                open: this.props.open
            })
        } 
    }

    collapseOpen() {
        this.setContentHeight()
        if (this.props.onChange) {
            this.props.onChange(!this.state.open)
        } else {
            this.setState({
                open: !this.state.open
            })
        }
        
        this.forceUpdate();
    }

    render() {
        return (
            <div className={`fui-collapse ${this.state.open ? 'is-open' : ''}`}>
                <div 
                role="button"
                onClick={this.collapseOpen} 
                className={`collapse-header`}>
                    {this.props.title}
                </div>
                <div 
                className="collapse-body" 
                style={{
                    height: this.state.open ? this.state.contentHeight : 0
                }}>
                    <article ref={this.body}  dangerouslySetInnerHTML={{__html: this.props.content}}></article>
                </div>
            </div>
        )
    }
}

Collapse.propTypes = {
    title: PropTypes.string.isRequired,
    content: PropTypes.string.isRequired,
    open: PropTypes.bool,
    children: PropTypes.node,
    date: PropTypes.string,
    open: PropTypes.bool
}

export default Collapse
```
{% endcode %}

#### Properties

| 名稱     | 屬性    | 必填 | 選項 | 說明                    |
| :------- | :------ | :--- | :--- | :---------------------- |
| title    | String  | true |      | 標題                    |
| content  | String  | true |      | 內文，直接輸入 HTML標題 |
| children | node    |      |      |                         |
| date     | string  |      |      |                         |
| open     | Boolean |      |      |                         |

## Related Components

* CollapsePanel
* CollapseMenu
* SectionFaq

## SectionCollapseInfo

![](../.gitbook/assets/image%20%28215%29.png)



{% tabs %}
{% tab title="React JSX" %}
{% code title="SectionCollapseInfo.js" %}
```jsx
import SectionCollapseInfo from '../../components/partials/collapse/SectionCollapseInfo';
<SectionCollapseInfo
            title="貼心小叮嚀"
            theme="dark"
            bgColor="#000"
            content={`
                <ol>
                  <li>此功能不需帳號及密碼，只要輸入身分資料完成登入檢核就可進行繳款。</li>
                  <li>快速登入後僅能進行繳款功能，若需使用其他功能，請先進行登入。</li>
                  <li>繳納費用非一般性消費支出，請洽各發卡銀行確認是否有刷卡紅利或現金回饋。</li>
                </ol>
              `}
          />
```
{% endcode %}
{% endtab %}

{% tab title="" %}
```jsx
import React from 'react';
import Collapse from '../../collapse/Collapse';

import PropTypes from 'prop-types'

class SectionCollapseInfo extends React.Component {
    constructor(props) {
        super(props)
        this.state = {
            current: 0
        }
    }

    render() {
        return (
            <section style={this.props.bgColor ? { backgroundColor: this.props.bgColor } : null} className={`fui-section-collapse ${this.props.className ? this.props.className : ''} ${this.props.theme ? ('is-' + this.props.theme) : ''}`}>
                <div className="fui-container">
                    <Collapse
                        title={this.props.title}
                        content={this.props.content} />
                </div>
            </section>
        )
    }
}

SectionCollapseInfo.propTypes = {
    title: PropTypes.string,
    className: PropTypes.string,
    content: PropTypes.string
}

export default SectionCollapseInfo;
```
{% endtab %}
{% endtabs %}



#### Properties

| 名稱      | 屬性   | 必填  | 選項           | 說明         |
| :-------- | :----- | :---- | :------------- | :----------- |
| title     | String | true  |                | 標題         |
| className | String | false |                |              |
| content   | String | false |                |              |
| theme     | String | false | 'light','dark' | 黑色白色佈景 |
| bgColor   | String | false | \#fff          | 背景色       |

## CollapseDiscount

```
import CollapseDiscount from '../../components/collapse/CollapseDiscount';
<CollapseDiscount list={...[
    {
      name: '(換)特殊通路限定_新絕配199_限24_單門號',
      startDate: '2017/12/21',
      endDate: '2020/06/20',
      contractLimit: '2021/08/09後方可更改低於4G新絕配199',
      contractSuspendInfoList: null,
      contractDiscountInfoList: [
        {
          name: '上網傳輸輛優惠3GB*24個月',
          startDate: '2019/08/08',
          endDate: '2021/08/20',
        },
        {
          name: '網內通話優惠200分鐘*24個月',
          startDate: '2019/08/08',
          endDate: '2021/08/20',
        },
        {
          name: '他網通話優惠20分鐘*24個月',
          startDate: '2019/08/08',
          endDate: '2021/08/20',
        },
        {
          name: '市話通話優惠5分鐘*24個月',
          startDate: '2019/08/08',
          endDate: '2021/08/20',
        },
      ],
    },
    {
      name: '4G絕配平板方案_高速飆網899_限24_平板案',
      startDate: '2018/11/27',
      endDate: '2020/11/26',
      contractLimit: '2020/11/26後方可更改低於4G高速飆網899',
      contractSuspendInfoList: null,
      contractDiscountInfoList: [
        {
          name: 'Wifly/FET-WiFi免費優惠',
          startDate: '2018/11/27',
          endDate: '無使用期限',
        },
        {
          name: '上網傳輸量優惠5.5GB*24個月',
          startDate: '2018/11/27',
          endDate: '2020/12/25',
        },
        {
          name: '上網傳輸量優惠15GB*24個月',
          startDate: '2018/11/27',
          endDate: '2020/12/25',
        },
      ],
    },
  ] } />
```

| 名稱 | 屬性  | 選項 | 必填 | 說明 |
| :--- | :---- | :--- | :--- | :--- |
| list | array |      |      |      |

## CollapsePaper

```
import CollapsePaper from '../../components/collapse/CollapsePaper'
<CollapsePaper
title="全部應繳"
className="barcode-paper"
openCollapse={e => { console.log(e) }}
open={true}
>
<div className="subtitle">
<div className="float-right payment-price">1,199元</div>
總金額
</div>
<img src={process.env.PUBLIC_URL + '/resources/cbu/e-service/images/barcode-1.png'} alt='' className="barcode-img my-1" />
<div className="align-center pb-2">
<small className="body2 is-text-gray100">超商繳費條碼</small>
</div>
</CollapsePaper>
```

| 名稱         | 屬性   | 選項 | 必填 | 說明 |
| :----------- | :----- | :--- | :--- | :--- |
| className    | string |      |      |      |
| title        | string |      | true |      |
| open         | bool   |      |      |      |
| children     | any    |      |      |      |
| openCollapse | func   |      |      |      |
| date         | string |      |      |      |


## FaqCollapse

```
import FaqCollapse from '../../components/collapse/FaqCollapse';
<FaqCollapse
    key={`faq-collapse-${j}`}
    title={faq.title}
    content={faq.content}
    detailLink={faq.detailLink}
    open={i === 0 && j === 0}
    feedback={e => console.log(e)}
/>
```

| 名稱        | 屬性   | 選項          | 必填 | 說明 |
| :---------- | :----- | :------------ | :--- | :--- |
| title       | string |               | true |      |
| content     | string |               | true |      |
| detailLink  | string |               |      |      |
| feedback    | func   |               |      |      |
| open        | bool   | default false |      |      |
| hasFeedback | bool   |               |      |      |

## ReceiptCollapse

```
import ReceiptCollapse from '../../components/collapse/ReceiptCollapse';
<ReceiptCollapse {... [
  {
    date: '2020/03/28',
    name: '台北市公有停車場費(PTP-20200328000000443187)',
    meta: {
      type: '計次型',
      number: 'CLP00063200328123778',
      hasReceipt: false,
    },
    amount: 90,
    detail: [
      { text: '日期：2020/03/28' },
      { text: '商家名稱：台北市停車管理工程處' },
      { text: '商家電話：02-2726-9600' },
      { text: '金額：90元' },
      { text: '付款方式：電信帳單付款' },
      { text: '交易狀態：成功' },
    ]
  },
  {
    date: '2020/03/28',
    name: '台北市公有停車場費(PTP-20200328000000443187)',
    meta: {
      type: '計次型',
      number: 'CLP00063200328123778',
      hasReceipt: false,
    },
    amount: 30,
    detail: [
      { text: '日期：2020/03/28' },
      { text: '商家名稱：台北市停車管理工程處' },
      { text: '商家電話：02-2726-9600' },
      { text: '金額：90元' },
      { text: '付款方式：電信帳單付款' },
      { text: '交易狀態：成功' },
    ]
  }
]} openModal={this.openModal} key={`receipt-collapse-${i}`} layout='record' />
```

#### Properties

| 名稱        | 屬性   | 選項 | 必填 | 說明 |
| :---------- | :----- | :--- | :--- | :--- |
| date        | string |      |      |      |
| name        | string |      |      |      |
| layout      | string |      |      |      |
| meta        | obj    |      |      |      |
| amount      | number |      |      |      |
| detail      | array  |      |      |      |
| openInvoice | func   |      |      |      |


## ResponseCollapse

```
import ResponseCollapse from '../collapse/ResponseCollapse';
<ResponseCollapse
    title={menu.title}
    list={menu.list}
    open={i === 0 ? true : false}
    id={`lookforArea-${i + 1}`}
/>
```

#### Properties

| 名稱  | 屬性   | 選項 | 必填 | 說明                                                                                           |
| :---- | :----- | :--- | :--- | :--------------------------------------------------------------------------------------------- |
| title | string |      | true |                                                                                                |
| list  | array  |      | true | text: PropTypes.string,link: PropTypes.string,target: PropTypes.string,icon: PropTypes.string, |
| open  | bool   |      |      |                                                                                                |
