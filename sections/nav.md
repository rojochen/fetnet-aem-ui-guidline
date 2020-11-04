# Nav

### Nav-anchor

在header帶有產品/服務名稱的單頁錨點導航列，可依需求編輯欄位:

* 大標 \(可選擇上字或圖片, 字數限制=10, 圖片限制高度40px, 寬度自動縮放\)
* 選項 \(可增減選項2-5項\)
* 按鈕 \(字數限制=10\)

小網只顯示大標和按鈕,，隱藏選項.

![](../.gitbook/assets/image%20%28224%29.png)

{% tabs %}
{% tab title="Usage" %}
```jsx
import NavAnchor from '../components/partials/NavAnchor';

<NavAnchor
  pageTitle='遠傳商務服務網站地圖'
  tabs={[
    { label: '產品與服務', link: '#products' },
    { label: '企業解決方案', link: '#solution' },
    { label: '趨勢觀點', link: '#tech' },
    { label: '幫助中心', link: '#help' },
    { label: '5G', link: '#fiveg' },
    { label: '優惠', link: '#discount' },
  ]}
/>
```
{% endtab %}

{% tab title="NavTab.js" %}
```jsx
import React from 'react';
import { Link } from 'react-router-dom';
import { setScroll, setScrollY, setHash } from '../../stores/actions';
import { connect } from 'react-redux';
import Button from '../Button';
import PropTypes from 'prop-types';

class NavAnchor extends React.Component {
  constructor(props) {
    super(props);
    this.elem = React.createRef();
    this.anchor = React.createRef();
    this.state = {
      defaultTop: 0,
      scrollPos: 0,
    };

    this.doHashChange = this.doHashChange.bind(this);
  }

  doHashChange(tab, index) {
    Array.from(this.anchor.current.children).forEach((elem, i) => {
      if (index === i) elem.classList.add('is-active');
      else elem.classList.remove('is-active');
    });
  }

  componentDidMount() {
    this.setState({
      defaultTop:
        window.innerWidth < 960 ? 50 : this.elem.current.offsetTop || this.elem.current.parentElement.offsetTop,
    });

    window.addEventListener('resize', e => {
      if (this.elem.current) {
        this.setState({
          defaultTop:
            window.innerWidth < 960 ? 50 : this.elem.current.offsetTop || this.elem.current.parentElement.offsetTop,
        });
      }

      var isMobile = window.innerWidth < 960;
      let lastIndex = 0;

      if (this.props.tabs) {
        this.props.tabs.forEach((tab, i) => {
          let elem = document.getElementById(tab.link.slice(1));
          // console.log( this.anchor.current)
          if (elem && null!==this.anchor.current) {
            let anchor = this.anchor.current.children[i];
            let y = window.scrollY || document.documentElement.scrollTop;
            if (!isMobile) {
              if (elem.offsetTop - 100 <= y && elem.offsetTop + elem.clientHeight - 150 >= y) {
                anchor.classList.add('is-active');
              } else {
                anchor.classList.remove('is-active');
              }
            } else {
              if (elem.offsetTop - 100 <= y) lastIndex = i;
            }
          }
        });
      }
    });

    window.addEventListener('scroll', e => {
      if (!this.elem.current) {
        return;
      }

      let scrollY = window.scrollY || document.documentElement.scrollTop;
      let headerDom = document.getElementsByTagName('header')[0];
      let header = headerDom.clientHeight;
      let dis = this.state.defaultTop - scrollY;

      if (scrollY > this.state.scrollPos && scrollY > 0) {
        headerDom.style.transform = `translateY(${-scrollY < -header ? -header : -scrollY}px)`;

        if (scrollY >= header) {
          this.elem.current.classList.add('is-fixed');
        }
      }

      if (scrollY < this.state.scrollPos && scrollY < this.state.defaultTop + header) {
        this.elem.current.classList.remove('is-fixed');
        headerDom.style.transform = `translateY(${-scrollY >= 0 ? 0 : -scrollY}px)`;
      }

      this.setState({ scrollPos: scrollY });

      let isMobile = window.innerWidth < 960;
      let lastIndex = 0;

      if (this.props.tabs) {
        this.props.tabs.forEach((tab, i) => {
          if (tab.link.indexOf('#') === -1) return;
          if(document.getElementById((tab.link).slice(1))) {
            let elem = document.getElementById((tab.link).slice(1));
            
            let anchor = this.anchor.current.children[i];
            let y = window.scrollY || document.documentElement.scrollTop;
            if (!isMobile) {
              if (elem.offsetTop - 100 <= y && elem.offsetTop + elem.clientHeight - 150 >= y) {
                anchor.classList.add('is-active');
              } else {
                anchor.classList.remove('is-active');
              }
            } else {
              if (elem.offsetTop - 100 <= y) lastIndex = i;
            }
          }
        });
      }

      if (isMobile) {
        Array.from(this.anchor.current.children).forEach((item, i) => {
          if (i === lastIndex) item.classList.add('is-active');
          else item.classList.remove('is-active');
        });
      }
    });
  }

  render() {
    return (
      <div className={`fui-nav-anchor`} ref={this.elem}>
        <div className='fui-container'>
          <div className='content'>
            <div className='subtitle' dangerouslySetInnerHTML={{ __html: this.props.pageTitle }}></div>
            <div className='page-anchor' ref={this.anchor}>
              {this.props.tabs
                ? this.props.tabs.map((tab, i) => (
                    <Link
                      to={tab.link}
                      key={`page-anchor-${i}`}
                      className={`page-anchor-item ${tab.link === window.location.pathname ? 'is-active' : ''}`}
                      onClick={e => this.doHashChange(tab, i)}>
                      {tab.label}
                    </Link>
                  ))
                : null}
            </div>
          </div>
          <div className='extra'>
            {!this.props.button === false && this.props.button.text ? (
              <Button {...this.props.button} size='small' btnStyle='secondary'>
                {this.props.button.text}
              </Button>
            ) : (
              ''
            )}
          </div>
        </div>
      </div>
    );
  }
}

NavAnchor.propTypes = {
  pageTitle: PropTypes.string,
  tabs: PropTypes.arrayOf(
    PropTypes.shape({
      label: PropTypes.string,
      link: PropTypes.string,
    })
  ),
  button: PropTypes.shape({
    link: PropTypes.string,
    text: PropTypes.string,
  }),
  onChange: PropTypes.func,
};

function mapStateToProps(state, ownProps) {
  // debugger
  const { AnchorScroll } = state;
  return {
    ...AnchorScroll,
  };
}

export default connect(mapStateToProps, { setScroll, setScrollY, setHash })(NavAnchor);

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
      <th style="text-align:left">&#x8AAA;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">pageTitle</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x9801;&#x9762;&#x540D;&#x7A31;</td>
    </tr>
    <tr>
      <td style="text-align:left">tabs</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left">
        <p>{</p>
        <p>label: String,</p>
        <p>link: String</p>
        <p>}</p>
      </td>
      <td style="text-align:left">&#x8981;&#x5C0E;&#x5165;&#x7684;&#x9023;&#x7D50;</td>
    </tr>
    <tr>
      <td style="text-align:left">button</td>
      <td style="text-align:left">Object</td>
      <td style="text-align:left">
        <p>{</p>
        <p>text: String,</p>
        <p>link: String</p>
        <p>}</p>
      </td>
      <td style="text-align:left">&#x6309;&#x9215;</td>
    </tr>
    <tr>
      <td style="text-align:left">onChange</td>
      <td style="text-align:left">Function</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x5207;&#x63DB;&#x9078;&#x9805;&#x6642;&#x56DE;&#x50B3;&#x503C;</td>
    </tr>
  </tbody>
</table>

### Nav-tab

在header帶有產品/服務名稱的頁面切換導航列，可依需求編輯欄位：

* 大標 \(可選擇上字或圖片, 字數限制=10, 圖片限制高度40px, 寬度自動縮放\)
* 選項 \(可增減選項2-5項\)
* 按鈕 \(字數限制=10\)

小網只顯示大標和按鈕,，隱藏選項

![](../.gitbook/assets/image%20%28152%29.png)

{% tabs %}
{% tab title="Usage" %}
```jsx
import NavTab from '../components/partials/NavTab';

<NavTab
  pageTitle='幫助中心'
  onChange={this.tabChange}
  default={this.state.currentTab}
  tabs={{
    name: 'help-center-tab',
    list: [
      { name: 'help-cbu', label: '個人用戶' },
      { name: 'help-ebu', label: '企業用戶' },
      { name: 'help-contact', label: '聯絡我們' },
    ],
  }}
  button={{
    text: '回首頁',
    link: '/help-center',
  }}
/>
```
{% endtab %}

{% tab title="NavTab.js" %}
```jsx
import React from 'react';
import DropdownTab from '../tab/DropdownTab';
import Button from '../Button';
import PropTypes from 'prop-types';

class NavTab extends React.Component {
  constructor(props) {
    super(props);
    this.elem = React.createRef();
    this.state = {
      defaultTop: 52,
      scrollPos: 0,
    };
  }

  componentDidMount() {
    let header = document.getElementsByTagName('header')[0]
    this.setState({
      defaultTop: header.clientHeight,
    });

    window.addEventListener('resize', e => {
      if (!this.elem.current) return;
      this.setState({
        defaultTop: header.clientHeight,
      });
    });
    
    window.addEventListener('scroll', e => {
      if (!this.elem.current) return;
  
      let headerDom = document.getElementsByTagName('header')[0]
      let scrollY = window.scrollY || document.documentElement.scrollTop;
      let header = headerDom.clientHeight;
      
      if (scrollY > this.state.scrollPos && scrollY > 0) {
        headerDom.style.transform = `translateY(${-scrollY < -header ? -header : -scrollY}px)`;

        if (scrollY >= header) {
          this.elem.current.classList.add('is-fixed');
        }
      }

      if (scrollY < this.state.scrollPos && scrollY < this.state.defaultTop + header) {
        this.elem.current.classList.remove('is-fixed');
        headerDom.style.transform = `translateY(${-scrollY >= 0 ? 0 : -scrollY}px)`;
      }

      this.setState({ scrollPos: scrollY });
    });

  }

  handleChange(value) {
    if (this.props.onChange) {
      this.props.onChange(value);
    }
  }

  render() {
    return (
      <div className='fui-nav-tab' ref={this.elem}>
        <div className='fui-container'>
          <div className='content'>
            <div className='subtitle'>{this.props.pageTitle}</div>
            {this.props.tabs ? (
              <DropdownTab tabs={this.props.tabs} default={this.props.default} onChange={e => this.handleChange(e)} />
            ) : null}
          </div>
          <div className='extra'>
            {this.props.button ? (
              <Button {...this.props.button} size='small' btnStyle='secondary'>
                {this.props.button.text}
              </Button>
            ) : (
              ''
            )}
          </div>
        </div>
      </div>
    );
  }
}

NavTab.propTypes = {
  showAll: PropTypes.bool,
  pageTitle: PropTypes.string,
  default: PropTypes.number,
  tabs: PropTypes.shape({
    name: PropTypes.string,
    list: PropTypes.arrayOf(
      PropTypes.shape({
        icon: PropTypes.string,
        focusIcon: PropTypes.string,
        label: PropTypes.string.isRequired,
        link: PropTypes.string
      })
    ),
  }),
  button: PropTypes.shape({
    link: PropTypes.string,
    text: PropTypes.string,
  }),
  onChange: PropTypes.func,
};

export default NavTab;

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
      <th style="text-align:left">&#x8AAA;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">pageTitle</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x9801;&#x9762;&#x540D;&#x7A31;</td>
    </tr>
    <tr>
      <td style="text-align:left">default</td>
      <td style="text-align:left">Number</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x9810;&#x8A2D;&#x88AB;&#x9078;&#x53D6;&#x7684;&#x9801;&#x7C64;</td>
    </tr>
    <tr>
      <td style="text-align:left">tabs</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left">
        <p>{</p>
        <p>label: String,</p>
        <p>link: String,</p>
        <p>}</p>
      </td>
      <td style="text-align:left">&#x8981;&#x5C0E;&#x5165;&#x7684;&#x9023;&#x7D50;</td>
    </tr>
    <tr>
      <td style="text-align:left">button</td>
      <td style="text-align:left">Object</td>
      <td style="text-align:left">
        <p>{</p>
        <p>text: String,</p>
        <p>link: String</p>
        <p>}</p>
      </td>
      <td style="text-align:left">&#x6309;&#x9215;</td>
    </tr>
    <tr>
      <td style="text-align:left">onChange</td>
      <td style="text-align:left">Function</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x5207;&#x63DB;&#x9078;&#x9805;&#x6642;&#x56DE;&#x50B3;&#x503C;</td>
    </tr>
  </tbody>
</table>

### **Nav-content-tab-1**

Tab型式的單頁導航列，可依需求編輯欄位：

* 選項 \(每個選項字元限制=10，可增減選項2-5項\) 畫面捲動至上方時會將header推開，並固定在頂端。

小網推到頂端時會顯示大標和按鈕

![](../.gitbook/assets/image%20%28118%29.png)

{% tabs %}
{% tab title="Usage" %}
```jsx
import NavContentTab1 from '../components/partials/NavContentTab1';

<NavContentTab1
  tabs={{
    name: 'zipcode-tab',
    list: [
      { name: 'tab-1', label: '國內區碼' },
      { name: 'tab-2', label: '世界國碼' },
      { name: 'tab-3', label: '中國城市區碼' },
    ],
  }}
  onChange={this.tabChange}
/>

```
{% endtab %}

{% tab title="NavContentTab1" %}
```jsx
import React from 'react';
import Button from '../Button';
import DropdownTab from '../tab/DropdownTab';

import PropTypes from 'prop-types';

class NavContentTab1 extends React.Component {
  constructor(props) {
    super(props);
    this.elem = React.createRef();
    this.state = {
      defaultTop: 0,
      scrollPos: 0,
    };

  }

  componentDidMount() {
    this.setState({
      defaultTop: this.elem.current.offsetTop,
    });

    window.addEventListener('resize', e => {
      if (!this.elem.current) return;
      this.setState({
        defaultTop: document.getElementsByTagName('header')[0].clientHeight + document.getElementsByClassName('fui-banner')[0].clientHeight,
      });
    });

    window.addEventListener('scroll', e => {
      if (!this.elem.current) return;

        let scrollY = window.scrollY || document.documentElement.scrollTop;
        let dis = this.state.defaultTop - scrollY;
        let headerDom = document.getElementsByTagName('header')[0];
        let header = headerDom.clientHeight;

        if (scrollY > this.state.scrollPos && scrollY > this.state.defaultTop) {
          headerDom.style.transform = `translateY(${dis < -header ? -header : dis}px)`;

          if (scrollY > this.state.defaultTop + header) {
            this.elem.current.classList.add('is-fixed');
          }
        }

        if (scrollY < this.state.scrollPos && scrollY < this.state.defaultTop + header) {
          this.elem.current.classList.remove('is-fixed');
          headerDom.style.transform = `translateY(${dis > 0 ? 0 : dis}px)`;
        }

        this.setState({ scrollPos: scrollY });
      
    });
  }

  handleChange(value) {
    if (this.props.onChange) {
      this.props.onChange(value);
    }
  }

  render() {
    return (
      <div className='fui-nav-tab is-content-1' ref={this.elem}>
        <div className='fui-container'>
          <div className='content'>
            <div className='subtitle'>{this.props.pageTitle}</div>
            <DropdownTab tabs={this.props.tabs} default={this.props.default} onChange={e => this.handleChange(e)} />
          </div>
          <div className='extra'>
            {this.props.button ? (
              <Button {...this.props.button} size='small' btnStyle='secondary'>
                {this.props.button.text}
              </Button>
            ) : (
              ''
            )}
          </div>
        </div>
      </div>
    );
  }
}

NavContentTab1.propTypes = {
  default: PropTypes.number,
  tabs: PropTypes.shape({
    name: PropTypes.string,
    list: PropTypes.arrayOf(
      PropTypes.shape({
        icon: PropTypes.string,
        focusIcon: PropTypes.string,
        label: PropTypes.string.isRequired,
        link: PropTypes.string
      })
    ),
  }),
  onChange: PropTypes.func,
};

export default NavContentTab1;

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
      <th style="text-align:left">&#x8AAA;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">default</td>
      <td style="text-align:left">Number</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x9810;&#x8A2D;&#x88AB;&#x9078;&#x53D6;&#x7684;&#x9801;&#x7C64;</td>
    </tr>
    <tr>
      <td style="text-align:left">tabs</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left">
        <p>{</p>
        <p>name: String,</p>
        <p>list: [
          <br />{</p>
        <p>label: String,
          <br />link: String
          <br />}</p>
        <p>]</p>
        <p>}</p>
      </td>
      <td style="text-align:left">
        <p>name: tab
          <br />list: tab &#x5217;&#x8868;</p>
        <p>- label : Tab &#x6587;&#x5B57;</p>
        <p>- link : &#x8981;&#x5C0E;&#x5165;&#x7684;&#x9023;&#x7D50;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">button</td>
      <td style="text-align:left">Object</td>
      <td style="text-align:left">
        <p>{</p>
        <p>text: String,</p>
        <p>link: String</p>
        <p>}</p>
      </td>
      <td style="text-align:left">&#x6309;&#x9215;</td>
    </tr>
    <tr>
      <td style="text-align:left">onChange</td>
      <td style="text-align:left">Function</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x5207;&#x63DB;&#x9078;&#x9805;&#x6642;&#x56DE;&#x50B3;&#x503C;</td>
    </tr>
  </tbody>
</table>

### Nav-content-tab-2

特殊Tab樣式，點選會切換上方Banner以及下方內容，可依需求編輯欄位：

* 圖片/圖標\(限制高度=30px\)
* 文字 \(每項字元限制=6，可增減選項為2-5項\)

![](../.gitbook/assets/image%20%285%29.png)

{% tabs %}
{% tab title="Usage" %}
```jsx
import NavContentTab2 from '../components/partials/NavContentTab2';

<NavContentTab2 tabs={{
    default: 2,
    name: 'solution-tab',
    icon: true,
    list: [
      {
        link: '/ebu/solution/food',
        name: 'solution-1',
        label: '餐飲',
        icon: '/resources/ebu/images/icon-chef.png',
        focusIcon: '/resources/ebu/images/icon-chef-focus.png',
      },
      {
        link: '/ebu/solution/retail',
        name: 'solution-2',
        label: '零售',
        icon: '/resources/ebu/images/icon-store.png',
        focusIcon: '/resources/ebu/images/icon-store-focus.png',
      },
      {
        link: '/ebu/solution/other',
        name: 'solution-3',
        label: '其他',
        icon: '/resources/ebu/images/icon-other.png',
        focusIcon: '/resources/ebu/images/icon-other-focus.png',
      },
    ],
  }} />
```
{% endtab %}

{% tab title="NavContentTab2.js" %}
```jsx
import React from 'react';
import Tab from '../tab/Tab';
import PropTypes from 'prop-types';

class NavContentTab2 extends React.Component {
  handleChange(value) {
    if (this.props.onChange) {
      this.props.onChange(value);
    }
  }
  render() {
    return (
      <div className={`fui-nav-tab is-box-tab`} ref={this.elem}>
        <Tab {...this.props.tabs} onChange={e => this.handleChange(e)} />
      </div>
    );
  }
}

NavContentTab2.propTypes = {
  tabs: PropTypes.shape({
    default: PropTypes.number,
    name: PropTypes.string.isRequired,
    icon: PropTypes.bool,
    title: PropTypes.bool,
    list: PropTypes.arrayOf(
      PropTypes.shape({
        icon: PropTypes.string,
        focusIcon: PropTypes.string,
        label: PropTypes.string.isRequired,
      })
    ).isRequired,
  }).isRequired,
  onChange: PropTypes.func,
};

export default NavContentTab2;

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
      <th style="text-align:left">&#x8AAA;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">tabs</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left">
        <p>{</p>
        <p>default: Number,</p>
        <p>icon: Boolean,</p>
        <p>title: String,</p>
        <p>list: [{</p>
        <p>icon: String,</p>
        <p>focusIcon: String,</p>
        <p>label: String,</p>
        <p>link: String,</p>
        <p>}]</p>
        <p>}</p>
      </td>
      <td style="text-align:left">
        <p>default: &#x9810;&#x8A2D;&#x9078;&#x53D6;&#x7684;&#x9805;&#x76EE;</p>
        <p>icon: &#x662F;&#x5426;&#x6709;icon</p>
        <p>list
          <br />- icon &#x5716;&#x6A19;
          <br />- focusIcon &#x5716;&#x6A19;&#x9078;&#x53D6;&#x6642;&#x7684;&#x72C0;&#x614B;
          <br
          />- label &#x6587;&#x5B57;</p>
        <p></p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">onChange</td>
      <td style="text-align:left">Function</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x5207;&#x63DB;&#x9078;&#x9805;&#x6642;&#x56DE;&#x50B3;&#x503C;</td>
    </tr>
  </tbody>
</table>

