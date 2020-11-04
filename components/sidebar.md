# Sidebar

## SelectedArticle

側邊欄樣式, 讀取最多6則內容, 欄位內規則 :

• 大標: 字符串長度&lt;20 \(20個字元\).   
• 標籤: 自動讀取  
• 日期欄位: 年/月/日 格式   
• 次標: 字符串長度&lt;70 最多2行 \(70個字元\).

• 最多顯示6則, 最少1則.

{% tabs %}
{% tab title="Web" %}
![](../.gitbook/assets/image%20%2871%29.png)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/image%20%2835%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Usage" %}
```jsx
import SelectedArticle from '../components/SelectedArticle';
import * as Mock from '../mock/Mock';

class NewsContent extends React.Component {
  render() {
    return (
      <SelectedArticle 
          article={Mock.selectedArticle.content} 
          title={Mock.selectedArticle.title} 
      />
    )
  }
}
```
{% endtab %}

{% tab title="Mock" %}
```javascript
export const selectedArticle = {
  title: '最新消息',
  content: [
    {
      id: '001',
      content: '冬季遊法浪漫旅，遠傳陪您遊法每日吃到飽399',
      genre: '活動',
      link: 'newsContentVersion2',
      date: {
        year: 2019,
        month: 12,
        day: 26,
      },
    },
    {
      id: '002',
      content: '遠傳愛講音箱 語音助理服務升級通知',
      genre: '公告',
      link: 'newsContentVersion2',
      date: {
        year: 2019,
        month: 12,
        day: 26,
      },
    },
    {
      id: '003',
      content: '遠傳電信帳單代收服務全面支援「訂閱經濟」',
      genre: '業務',
      link: 'newsContentVersion2',
      date: {
        year: 2019,
        month: 12,
        day: 26,
      },
    },
    {
      id: '004',
      content: '紐西蘭/澳洲遠遊卡超值上市每日上網吃到飽只要$38',
      genre: '業務',
      link: 'newsContentVersion2',
      date: {
        year: 2019,
        month: 12,
        day: 26,
      },
    },
    {
      id: '005',
      content: '雙11鳴槍 遠傳易付卡大放送！上網流量買1送1',
      genre: '業務',
      link: 'newsContentVersion2',
      date: {
        year: 2019,
        month: 12,
        day: 26,
      },
    },
    {
      id: '006',
      content: '遠傳好「錶」現 Apple Watch Series 5 LTE開賣',
      genre: '業務',
      link: 'newsContentVersion2',
      date: {
        year: 2019,
        month: 12,
        day: 26,
      },
    },
  ],
};

```
{% endtab %}

{% tab title="React JSX" %}
{% code title="SelectedArticle.js" %}
```jsx
import React from 'react';
import { Link } from 'react-router-dom';
import PropTypes from 'prop-types';

class SelectedArticle extends React.Component {
  render() {
    return (
      <div className='selected-article'>
        <div className='head'>
          <h6>{this.props.title}</h6>
        </div>
        <ul>
          {this.props.article.map(article => {
            return (
              <li key={article.id}>
                <Link to={article.link}>
                  {article.genre ? (
                    <div className='top'>
                      <small>{article.genre}</small>
                      <small>
                        {article.date.year}/{article.date.month}/{article.date.day}
                      </small>
                    </div>
                  ) : (
                    ''
                  )}
                  <div className='body'>
                    <p>{article.content}</p>
                    <i className='icon-chevron-right'></i>
                  </div>
                </Link>
              </li>
            );
          })}
        </ul>
      </div>
    );
  }
}

SelectedArticle.propTypes = {
  title: PropTypes.string,
  article: PropTypes.array,
};
export default SelectedArticle;

```
{% endcode %}
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
      <td style="text-align:left">&#x6A21;&#x7D44;&#x6A19;&#x984C;</td>
    </tr>
    <tr>
      <td style="text-align:left">article</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>{
          <br />id: number or string,</p>
        <p>link: string, &#xFF08;&#x5FC5;&#x586B;&#xFF09;</p>
        <p>genre: string,</p>
        <p>date: {</p>
        <p>year,</p>
        <p>month,</p>
        <p>day</p>
        <p>},</p>
        <p>content: string&#xFF08;&#x5FC5;&#x586B;&#xFF09;
          <br />}</p>
      </td>
      <td style="text-align:left">&#x82E5;&#x6709; genre&#xFF0C;&#x5247;&#x5E36;&#x5165; date</td>
    </tr>
  </tbody>
</table>

## CollapseMenu

過濾左側或右側內容的側邊欄樣式, 可以需求調整欄位:  
• 大標: 字符串長度&lt;20 \(20個字元\)  
• 可增加條列項目, 並限制字元行數=1  
• 條列項目可增加第二層分類, 增加後上層會出現下拉箭頭  
• 已點選狀態下條列項目樣式改變 \(文字變色\)

{% tabs %}
{% tab title="Web" %}
第一層樣式 ／第一層展開樣式／點選第二層樣式

![](../.gitbook/assets/image%20%28154%29.png)
{% endtab %}

{% tab title="Mobile" %}
第一層樣式 ／第一層展開樣式／點選第二層樣式

![](../.gitbook/assets/image%20%28229%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Usage" %}
```jsx
import CollapseMenu from '../components/partials/collapse/CollapseMenu';
import * as Mock from '../mock/Mock';


class Page extends React.Component {
  changeMenu = value => {
    console.log(value);
  };
  
  render () {
    return (
      <CollapseMenu menu={Mock.menu} selectMenu={this.changeMenu} />
    )
  }
}
```
{% endtab %}

{% tab title="Mock" %}
```javascript
export const menu = {
  id: 1,
  name: '常見問題分類',
  content: [
    {
      id: 11,
      name: '熱門常見問題',
      link: '/help-center/faq',
    },
    {
      id: 12,
      name: '007國際電話',
      link: '/help-center/faq/007',
    },
    {
      id: 13,
      name: '1807國內長途電話',
      link: '/help-center/faq/1807',
    },
    {
      id: 14,
      name: 'Office365',
      link: '/help-center/faq/office365',
    },
    {
      id: 15,
      name: '大寬頻ADSL',
      link: '/help-center/faq/adsl',
    },
    {
      id: 16,
      name: '大寬頻企業光纖',
      link: '/help-center/faq/web',
    },
    {
      id: 17,
      name: '主機代管',
      link: '/help-center/faq/server',
    },
    {
      id: 18,
      name: '中小企業資訊委外',
      link: '/help-center/faq/outsource',
    },
    {
      id: 19,
      name: '視訊會議雲',
      link: '/help-center/faq/cammeeting',
    },
    {
      id: 20,
      name: '雲端運算',
      link: '/help-center/faq/cloud',
    },
    {
      id: 21,
      name: '雲端電話/網路會議',
      link: '/help-center/faq/webmeeting',
    },
    {
      id: 22,
      name: '遠傳物聯網',
      link: '/help-center/faq/iot',
    },
  ],
};
```
{% endtab %}

{% tab title="CollapseMenu.js" %}
```jsx
import React, { Component } from 'react';
import { NavLink } from 'react-router-dom';
import PropTypes from 'prop-types';

export class CollapseMenu extends Component {
  constructor(props) {
    super(props)
    this.state = {
      isMobile: window.innerWidth < 960,
      showMore: false,
      toggle: false,
      toggleMenu: false,
      activeLevel: [0, -1],
      openLevel: -1,
      currentGroup: null,
      currentSelected: null
    }
  }

  componentDidMount() {
    let open = this.state.openLevel;
    let menu = this.props.menu;
    let active = 0

    if (menu.content[0].link) {
      menu.content.map((m, i) => {
        if ((m.link).indexOf(window.location.pathname) > -1) {
          active = i
          this.setState({ activeLevel: [i, -1] })
        }
      })
    }

    this.setState({
      currentGroup: menu,
      openLevel: open,
      currentSelected: menu.content[active]
    })
  }

  selectedItem = (val, parent) => {
    let level = this.state.activeLevel;
    let toggle = this.state.toggleMenu;
    let open = this.state.openLevel;

    if (val.content) { // 處理子選單開闔
      toggle = (open === val.index) ? !toggle : true
      open = val.index
      this.setState({
        openLevel: open,
        toggleMenu: toggle
      })
    } else { // 處理子選單點選
      level[val.level] = val.index
      toggle = false

      if (parent)
        level[0] = parent
      else
        level[1] = -1

      this.setState({
        toggle: false,
        toggleLevel: toggle,
        activeLevel: level,
        currentSelected: val
      })

      this.props.selectMenu(val)
    }

    this.forceUpdate()
  }

  toggleMenu = () => {
    this.setState({
      toggle: !this.state.toggle
    })
  }

  toggleStatus = (val) => {
    let toggle = this.state.toggleMenu;
    let level = this.state.openLevel;
    return val === level && toggle ? 'menu-active' : ''
  }

  getActiveStatus = (val, parent) => {
    let active = this.state.activeLevel
    return ((parent && active[0] === parent) && active[1] === val) || (!parent && active[0] === val) ? 'active' : '';
  }

  render() {
    return (
      <div className={`fui-collapse-menu`}>
        <div className={`collapse-menu-group ${this.state.toggle ? 'menu-active' : ''}`}>
          <div className='collapse-menu-header'>
            <h6 className="group-name" onClick={this.toggleMenu}>
              {this.props.menu.name}
              <i className={`icon-${this.state.toggle ? 'minus' : 'plus'}`} />
            </h6>
            {!!this.state.currentSelected ? (
              <div className="current-select-item">
                <p className="body1">
                  {this.state.currentSelected.name}
                </p>
              </div>
            ) : null}
          </div>
          <ul>
            {this.props.menu.content.map((list, j) => {
              if(this.state.showMore || (j<10 && !this.state.showMore)) {
                if (!!list.content) {
                  return (
                    <li
                      className={`${this.toggleStatus(j, 1)}`}
                      key={`collapse-menu-child-${j}`}
                    >
                      <p
                        className="body1"
                        onClick={() => this.selectedItem({ level: 0, index: j, ...list })}
                      >
                        {list.name}
                        <i className={`icon-chevron-down`} />
                      </p>
                      <div className="item-group">
                        {list.content.map((item, k) => {
                          return item.link ? (
                            <NavLink exact to={item.link}
                              className={this.getActiveStatus(k, j)}
                              key={item.name}
                            >
                              {item.name}
                            </NavLink>
                          ) : (
                              <p
                                key={k}
                                onClick={() => this.selectedItem({ level: 0, index: j, ...list })}
                                className={this.getActiveStatus(k, j)}
                              >
                                {item.name}
                              </p>
                            )
                        })}
                      </div>
                    </li>
                  )
                } else {
                  return (
                    <li key={list.name}>
                      {
                        list.link ? (
                          <NavLink exact to={list.link}
                            className="body1"
                            onClick={() => this.selectedItem({ level: 0, index: j, ...list })}
                          >
                            {list.name}
                          </NavLink>
                        ) : (
                            <p
                              className={`body1 ${this.getActiveStatus(j, null)}`}
                              onClick={() => this.selectedItem({ level: 0, index: j, ...list })}>
                              {list.name}
                            </p>
                          )
                      }

                    </li>
                  )
                }
              }
            })}
            {
              (!this.state.showMore && this.props.menu.content.length > 10) ? (
                <li>
                  <p className='more-btn' onClick={e => this.setState({showMore: true})}>
                    <span className='text'>看更多</span> <i className="icon-plus"></i>
                  </p>
                </li>
              ) : null
            }
          </ul>
        </div>
      </div>
    );
  }
}

CollapseMenu.propTypes = {
  menu: PropTypes.shape({
    id: PropTypes.any,
    name: PropTypes.string.isRequired,
    content: PropTypes.arrayOf(
      PropTypes.shape({
        id: PropTypes.any,
        name: PropTypes.string.isRequired,
        link: PropTypes.string,
        content: PropTypes.arrayOf(
          PropTypes.shape({
            id: PropTypes.any,
            name: PropTypes.string,
            link: PropTypes.string
          })
        )
      })
    )
  }),
  selectMenu: PropTypes.func
}
export default CollapseMenu;

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
      <td style="text-align:left">default</td>
      <td style="text-align:left">Object</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>{</p>
        <p>id: &#x9078;&#x9805; ID</p>
        <p>name&#xFF1A;&#x9078;&#x55AE;&#x540D;&#x7A31;</p>
        <p>content: {
          <br />id: &#x5B50;&#x9078;&#x55AE; ID,
          <br />name: &#x5B50;&#x9078;&#x55AE;&#x540D;&#x7A31;,
          <br />link: &#x5B50;&#x9078;&#x55AE;&#x9023;&#x7D50;,</p>
        <p>content: &#x9078;&#x55AE;&#x5217;&#x8868;&#xFF0C;&#x4F9D;&#x6B64;&#x985E;&#x63A8;
          <br
          />}
          <br />}</p>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">selectMenu</td>
      <td style="text-align:left">Function</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x56DE;&#x50B3;&#x9078;&#x53D6;&#x7684;&#x9078;&#x9805;</td>
    </tr>
  </tbody>
</table>

## DropdownMenu

側邊欄下拉選單樣式

{% tabs %}
{% tab title="Web" %}
Default / 展開下拉選單樣式 / 點擊選項後收合樣式

![](../.gitbook/assets/image%20%28220%29.png)
{% endtab %}

{% tab title="Mobile" %}
Default / 展開下拉選單樣式 / 點擊選項後收合樣式

![](../.gitbook/assets/image%20%28206%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Usage" %}
```jsx
import DropdownMenu from '../components/partials/collapse/DropdownMenu';

class HelpCenterDocument extends React.Component {
  changeCategory = value => {
    console.log(value);
  };

  render() {
    return (
      <DropdownMenu 
      name='產品分類' 
      menu={Mock.dropdownMenu} 
      onChange={this.changeCategory} 
      />
    )
  }
}
```
{% endtab %}

{% tab title="Mock" %}
```javascript
export const dropdownMenu = {
  label: '選擇產品類別',
  list: [
    {
      text: '080免付費電話',
    },
    {
      text: '080免付費電話',
    },
    {
      text: '080免付費電話',
    },
    {
      text: '080免付費電話',
    },
    {
      text: '080免付費電話',
    },
  ],
};

```
{% endtab %}

{% tab title="React JSX" %}
{% code title="DropdownMenu.js" %}
```jsx
import React, { Component } from 'react';
import Dropdown from '../../Dropdown';
import PropTypes from 'prop-types';

export class CollapseMenu extends Component {
  constructor(props) {
    super(props);
    this.state = {
      isMobile: window.innerWidth < 960,
    };
  }

  dropdownChange = value => {
    this.props.onChange(value);
  };

  render() {
    return (
      <div className={`fui-collapse-menu is-dropdown`}>
        <div className='collapse-menu-header'>
          <h6 className='group-name d-none d-md-block ' onClick={this.toggleMenu}>
            {this.props.name}
          </h6>

          <Dropdown {...this.props.menu} arrow={true} onChange={this.dropdownChange} />
        </div>
      </div>
    );
  }
}

CollapseMenu.propTypes = {
  name: PropTypes.string.isRequired,
  menu: PropTypes.shape({
    label: PropTypes.string,
    list: PropTypes.arrayOf(
      PropTypes.shape({
        text: PropTypes.string.isRequired,
      })
    ),
  }),
  onChange: PropTypes.func,
};
export default CollapseMenu;

```
{% endcode %}
{% endtab %}
{% endtabs %}

#### Properties

| 名稱 | 屬性 | 必填 | 選項 | 說明 |
| :--- | :--- | :--- | :--- | :--- |
| name | String | true |  | 下拉選單 ID |
| menu | Object |  | {     label: String,     list: Array } | 資料結構請參考 [Dropdown](https://app.gitbook.com/@ajacreative/s/fetnet-1/~/drafts/-M1Poh4yStUSJuUM0OlJ/components/dropdown) ， list 只需要帶入 text |
| onChange | Function |  |  | 回傳選取的項目 |

