# Tab

Tab 用於將不同資料分類呈現，並減少網頁高度便於瀏覽。Tab 模組在 Fetnet 網頁使用為大宗，許多基本模組皆從此 tab 分散出去，建議不要輕易更動資料結構。若需要調整呈現，可透過父結構或 className 來做額外設定。

{% code title="Tab.js" %}
```jsx
import React from 'react';
import { Link } from 'react-router-dom';
import PropTypes from 'prop-types';

class Tab extends React.Component {
    constructor(props) {
        super(props);
        
        this.tabElem = React.createRef();
        this.rand = Math.round(Math.random() * 100)
        this.state = {
            visible: false,
            tabItemWidth: 0,
            hasLink: null !== this.props.list[0].link,
            currentPath: window.location.pathname,
            currentTab: this.props.default || 0,
            styles: {
                width: 0,
                left: 0
            }
        }
        
        this.setBarWidth = this.setBarWidth.bind(this)
    }

    componentDidMount() {
        if (this.state.hasLink && this.props.list && this.props.list.length) {
            this.setCurrentLink(window.location.pathname)
        }

        window.addEventListener('resize', () => { this.setBarWidth() })
    }
    
    componentDidUpdate(nextProps) {
        if (window.location.pathname !== this.state.currentPath) {
            this.setState({
                currentPath: window.location.pathname
            })
            this.setCurrentLink(window.location.pathname)
        }
        if (!this.isHidden(this.tabElem.current) !== this.state.visible && !this.state.visible) {
            this.setState({ visible: true })
            this.setBarWidth()
        }
    }

    setCurrentLink (path) {
        this.props.list.map((item, i) => {
            if (path === item.link) {
                this.setState({
                    currentTab: i
                })
            }
        })

        this.forceUpdate();
        setTimeout(() => {
            this.setBarWidth()
        }, 100)
    }

    setBarWidth() {
        if (!this.tabElem.current) return

        let item = this.tabElem.current.getElementsByClassName('is-active')[0];

        this.setState({
            styles: {
                ...this.state.styles,
                left: item.offsetLeft,
                width: Math.ceil(item.clientWidth)
            }
        })
    }

    isHidden = (el) => {
        return (el.offsetParent === null)
    }

    setScroller() {
        let container = this.tabElem.current
        let target = container.getElementsByClassName('is-active')[0]
        if (container.scrollLeft > target.offsetLeft) {
            if(window.isIE)
                container.scrollLeft = target.offsetLeft - 30
            else 
                container.scrollTo({
                    left: target.offsetLeft - 30,
                    top: 0,
                    behavior: 'smooth'
                })
        } else if (target.offsetLeft - (container.scrollLeft + container.clientWidth) < target.clientWidth) {
            if(window.isIE)
                container.scrollLeft = target.offsetLeft + target.clientWidth - container.clientWidth + 30
            else
                container.scrollTo({
                    left: target.offsetLeft + target.clientWidth - container.clientWidth + 30,
                    top: 0,
                    behavior: 'smooth'
                })
        }

    }

    handleChange(e, tab, newValue) {
        e.preventDefault();

        this.setState({
            currentTab: newValue,
            styles: {
                ...this.state.styles,
                width: this.tabElem.current.children[newValue + 1].clientWidth,
                left: this.tabElem.current.children[newValue + 1].offsetLeft
            }
        });

        if (this.props.onChange) {
            this.props.onChange(newValue)
        }

        this.forceUpdate()
        if (this.props.scroll && window.innerWidth < 960) {
            setTimeout(() => {
                this.setScroller()
            }, 50)
        }
    };

    render() {
        return (
            <div
                id={this.props.name}
                role='tablist'
                ref={this.tabElem}
                className={`fui-tab ${this.props.icon ? `with-icon` : ''} ${this.props.title ? `with-title` : ''} ${this.props.className ? this.props.className : ''} ${this.props.scroll ? 'with-scroller' : ''}`}
            >
                <div className="active-bar" style={this.state.styles}></div>
                {
                    this.props.list.map((tab, idx) => (
                        tab.link ? (
                            <Link
                                to={tab.link}
                                role="tab"
                                aria-selected={this.state.currentTab === idx}
                                className={`fui-tab-item ${this.state.currentTab === idx ? 'is-active' : ''}`}
                                key={`tab-${idx}`}
                                id={`tab-${this.rand}-${idx}`}
                            >
                                {tab.icon ? (
                                    <div>
                                        <div className="icon">
                                            <img src={tab.icon} className="default" alt={tab.icon} />
                                            <img src={tab.focusIcon} className="focus" alt={tab.icon} />
                                        </div>
                                        <div className="text">{tab.label}</div>
                                    </div>
                                ) : (
                                        <div>
                                            {tab.meta ? <small>{tab.meta}</small> : null}
                                            <div className="text">{tab.label}</div>
                                        </div>
                                    )}
                            </Link>
                        ) : (
                            <div
                                role="tab"
                                aria-selected={this.state.currentTab === idx}
                                onClick={e => this.handleChange(e, tab, idx)}
                                className={`fui-tab-item ${this.state.currentTab === idx ? 'is-active' : ''}`}
                                key={`tab-${idx}`}
                                id={`tab-${this.rand}-${idx}`}
                            >
                                {tab.icon ? (
                                    <div>
                                        <div className="icon">
                                            <img src={tab.icon} className="default" alt={tab.icon} />
                                            <img src={tab.focusIcon} className="focus" alt={tab.icon} />
                                        </div>
                                        <div className="text">{tab.label}</div>
                                    </div>
                                ) : (
                                        <div>
                                            {tab.meta ? <small>{tab.meta}</small> : null}
                                            <div className="text">{tab.label}</div>
                                        </div>
                                    )}
                            </div>
                        )
                    ))
                }
            </div>
        )
    }
}

Tab.propTypes = {
    scroll: PropTypes.bool,
    icon: PropTypes.bool,
    title: PropTypes.bool,
    className: PropTypes.string,
    name: PropTypes.string.isRequired,
    onChange: PropTypes.func,
    default: PropTypes.number,
    list: PropTypes.arrayOf(
        PropTypes.shape({
            icon: PropTypes.string,
            focusIcon: PropTypes.string,
            name: PropTypes.string.isRequired,
            label: PropTypes.string.isRequired,
            link: PropTypes.string
        })
    )
}

export default Tab;

```
{% endcode %}

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
      <td style="text-align:left">name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">true</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x4F5C;&#x70BA; Tab id &#x4F7F;&#x7528;&#xFF0C;&#x82E5;&#x540C;&#x4E00;&#x9801;&#x9762;&#x6709;&#x591A;&#x500B;
        Tab &#xFF0C;name &#x4E0D;&#x53EF;&#x91CD;&#x8907;</td>
    </tr>
    <tr>
      <td style="text-align:left">list</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>{
          <br />icon:String,</p>
        <p>focusIcon:String,
          <br />meta: String,
          <br />label: String,</p>
        <p>link: String
          <br />}</p>
      </td>
      <td style="text-align:left">
        <p>icon&#x3001;focusIcon &#x9700;&#x5728; <code>icon={true}</code> &#x7684;&#x6642;&#x5019;&#x4F7F;&#x7528;&#xFF0C;focusIcon
          &#x70BA; tab &#x88AB;&#x9078;&#x53D6;&#x72C0;&#x614B;&#x6642;&#xFF0C;icon
          &#x5716;&#x793A;
          <br />
          <br />meta: &#x5C0F;&#x6A19;&#xFF0C;&#x9810;&#x8A2D;&#x4E0D;&#x986F;&#x793A;
          <br
          />label: &#x6A19;&#x7C64;&#x6587;&#x5B57;&#xFF0C;&#x5FC5;&#x586B;
          <br />link: &#x6A19;&#x7C64;&#x9023;&#x7D50;&#xFF0C;&#x53EF;&#x4E0D;&#x586B;
          <br
          />
          <br />
        </p>
        <p></p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">icon</td>
      <td style="text-align:left">Boolean</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x53EF;&#x5E36;&#x5165;&#x6709; icon &#x7684;&#x6A23;&#x5F0F;&#xFF0C;&#x9810;&#x8A2D;&#x70BA; <code>false</code> &#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">title</td>
      <td style="text-align:left">Boolean</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x82E5; tab &#x4E0A;&#x65B9;&#x6709;&#x6A19;&#x984C;&#x5247;&#x4F7F;&#x7528; <code>title={true}</code> &#xFF0C;&#x6703;&#x5E36;&#x5165;&#x6A23;&#x5F0F;&#x6E1B;&#x5C11;&#x8207;&#x6A19;&#x984C;&#x7684;&#x9593;&#x8DDD;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">scroll</td>
      <td style="text-align:left">Boolean</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x5728;&#x5C0F;&#x7DB2;&#x6642;&#xFF0C;&#x662F;&#x5426;&#x7522;&#x751F;&#x5DE6;&#x53F3;&#x6372;&#x8EF8;&#xFF0C;&#x9810;&#x8A2D;&#x70BA; <code>false</code> &#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">default</td>
      <td style="text-align:left">Number</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x82E5; list &#x6C92;&#x5E36;&#x9023;&#x7D50;&#xFF0C;&#x53EF;&#x4EE5;&#x4F7F;&#x7528;
        default &#x9810;&#x8A2D;&#x88AB;&#x9078;&#x53D6;&#x7684;&#x9805;&#x76EE;&#x3002;&#x82E5;&#x6709;&#x5E36;&#x9023;&#x7D50;&#xFF0C;&#x6703;&#x4F9D;&#x64DA;&#x7DB2;&#x5740;&#x5224;&#x65B7;
        active &#x7684;&#x9805;&#x76EE;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">onChange</td>
      <td style="text-align:left">Function</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x56DE;&#x50B3;&#x76EE;&#x524D;&#x88AB;&#x9078;&#x53D6;&#x7684;&#x6A19;&#x7C64;</td>
    </tr>
  </tbody>
</table>

## Related Components

* [PanelTab](https://app.gitbook.com/@ajacreative/s/fetnet-1/~/drafts/-M1PX30KNQdcrffdEZXC/components/panel#panel-tab)
* DropdownTab
* ESectionTab
* NavContentTab2
* SolutionTab
* PromotionArticle

