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
    open: PropTypes.bool
}

export default Collapse
```
{% endcode %}

#### Properties

| 名稱 | 屬性 | 必填 | 選項 | 說明 |
| :--- | :--- | :--- | :--- | :--- |
| title | String | true |   | 標題 |
| content | String | true |  | 內文，直接輸入 HTML標題 |
| open | Boolean |  |  | 可從外部控制是否打開，預設為 `false` |

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

| 名稱 | 屬性 | 必填 | 選項 | 說明 |
| :--- | :--- | :--- | :--- | :--- |
| title | String | true |   | 標題 |
| className | String | false |  |  |
| content | String | false |  |  |
| theme | String | false | 'light','dark' | 黑色白色佈景 |
| bgColor | String | false | \#fff | 背景色 |

