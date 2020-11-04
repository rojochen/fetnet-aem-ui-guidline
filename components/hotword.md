---
description: 關鍵字搜尋元件
---

# Search

### HotWord

{% tabs %}
{% tab title="Desktop" %}
![](../.gitbook/assets/image%20%28242%29.png)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/image%20%28119%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Usage" %}
```javascript
import HotWord from '../components/HotWord';

<HotWord path='/help-center/faq' hotword={Mock.hotword} />
```
{% endtab %}

{% tab title="Source" %}
```javascript
import React from 'react';
import PropTypes from 'prop-types';
import { Link } from 'react-router-dom';

class HotWord extends React.Component {
  constructor(props) {
    super(props);
    this.keywords = React.createRef();
    this.state = {
      currentTab: 0,
      currentScroll: 0,
      scroller: false,
    };

    this.setScroller = this.setScroller.bind(this);
    this.doScroll = this.doScroll.bind(this);

    window.addEventListener('resize', e => this.setScroller);
  }

  componentDidMount() {
    this.setScroller();
  }

  detectLast() {
    if (!this.keywords.current) return false;
    return (
      this.state.currentScroll + this.keywords.current.clientWidth >= this.keywords.current.children[0].clientWidth
    );
  }

  doScroll = dir => {
    let clientW = this.keywords.current.clientWidth;
    if (window.isIE) {
      if (dir === 'left') this.keywords.current.scrollLeft = this.keywords.current.scrollLeft - clientW;
      if (dir === 'right') this.keywords.current.scrollLeft = this.keywords.current.scrollLeft + clientW;
    } else {
      if (dir === 'left')
        this.keywords.current.scrollTo({
          left: this.keywords.current.scrollLeft - clientW,
          top: 0,
          behavior: 'smooth',
        });
      if (dir === 'right')
        this.keywords.current.scrollTo({
          left: this.keywords.current.scrollLeft + clientW,
          top: 0,
          behavior: 'smooth',
        });
    }
    this.setState({ currentScroll: this.keywords.current.scrollLeft });
  };

  setScroller() {
    let outer = this.keywords.current.clientWidth;
    let inner = this.keywords.current.children[0].clientWidth;

    if (outer < inner) {
      this.setState({ scroller: true });

      this.keywords.current.addEventListener('scroll', e => {
        this.setState({ currentScroll: e.target.scrollLeft });
      });
    }
  }

  render() {
    return (
      <div className='keyword-container'>
        <div
          className={`keyword-list ${this.state.scroller ? 'is-scroller' : ''} ${
            this.state.currentScroll > 0 ? 'is-show-before' : ''
          } ${this.detectLast() ? 'is-hide-after' : ''}`}>
          <div className='label'>熱搜</div>
          <div className='keyword-content' ref={this.keywords}>
            <div className='keyword-group'>
              {this.props.hotword.map((word, i) => (
                <Link
                  role='button'
                  key={`hot-search-${i}`}
                  to={`${this.props.path}?keyword=${word}`}
                  className='fui-button is-label'>
                  {word}
                </Link>
              ))}
            </div>
          </div>
          {this.state.scroller ? (
            <div className='keyword-action'>
              <button
                onClick={e => {
                  this.doScroll('left');
                }}
                className={`fui-button is-text ${this.state.currentScroll === 0 ? 'disabled' : ''}`}>
                <i className='icon-chevron-left'></i>
              </button>
              <button
                onClick={e => {
                  this.doScroll('right');
                }}
                className={`fui-button is-text ${this.detectLast() ? 'disabled' : ''}`}>
                <i className='icon-chevron-right'></i>
              </button>
            </div>
          ) : (
            ''
          )}
        </div>
      </div>
    );
  }
}

HotWord.propTypes = {
  path: PropTypes.string,
  hotword: PropTypes.arrayOf(PropTypes.string),
};

export default HotWord;

```
{% endtab %}

{% tab title="Mock" %}
```javascript
export const hotword = [
  '遠傳物聯網',
  '雲端運算',
  '主機代管',
  '大寬頻企業',
  'Office 365',
  '007 國際電話',
  '007 國際電話',
  '007 國際電話',
  '大寬頻企業',
];
```
{% endtab %}
{% endtabs %}



#### Properties

| 名稱 | 屬性 | 必填 | 選項 | 說明 |
| :--- | :--- | :--- | :--- | :--- |
| path | string |  |  | 導至路徑 |
| hotword | array |  |  | 關鍵字列表 |

### KeywordInput

{% tabs %}
{% tab title="Desktop" %}
![](../.gitbook/assets/image%20%2865%29.png)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/image%20%28259%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Usage" %}
```javascript
import KeywordInput from '../KeywordInput';

<KeywordInput
  path='/help-center/search'
  keyword={this.state.keyword}
  placeholder='找企業用戶常見問題'
  defaultKeyword={[
    'Gogoro',
    'Gogoro 699',
    'google',
    'GPS',
    'GPS Google',
    'Gogo',
    'GoPro',
    'Geo',
    'SEO',
    'OPPO',
  ]}
/>
```
{% endtab %}

{% tab title="Source" %}
```javascript
import React from 'react';
import Autocomplete from 'react-autocomplete';
import Button from './Button';
import PropTypes from 'prop-types';

class KeywordInput extends React.Component {
  constructor(props) {
    super(props);
    const query = new URLSearchParams(window.location.search);
    this.input = React.createRef();
    this.state = {
      isEBU: window.location.pathname.indexOf('ebu') > -1,
      keywordMenu: this.props.defaultKeyword.slice(0, 6),
      keyword: query.get('keyword') || '',
    };

    this.doSearch = this.doSearch.bind(this);
  }

  highlightKeyword(word) {
    let value = this.state.keyword.toLowerCase();
    let index = word.toLowerCase().indexOf(value);

    if (index === -1 || value.value === '') {
      return word;
    } else {
      // console.log(word.substring(0,index) + "<span class='highlight'>" + word.substring(index,index+value.length) + "</span>" + word.substring(index + value.length))
      return (
        word.substring(0, index) +
        "<span class='highlight'>" +
        word.substring(index, index + value.length) +
        '</span>' +
        word.substring(index + value.length)
      );
    }
  }

  resetInput = () => {
    this.setState({
      keyword: '',
    });
  };

  doSearch(text) {
    window.location.href = `${this.props.path || '/ebu/search'}?keyword=${text || this.state.keyword}`;
  }

  render() {
    return (
      <div className='keyword-input-container'>
        {this.props.title ? <h2>{this.props.title}</h2> : ''}
        <Autocomplete
          wrapperStyle={{ width: '100%', position: 'relative' }}
          getItemValue={item => item}
          items={this.state.keywordMenu}
          value={this.state.keyword}
          onKeyDowe={this.inputChange}
          renderInput={props => (
            <div className={`fui-input-group is-keyword`}>
              <div className='fui-input'>
                <input ref={this.input} {...props} type='text' placeholder={this.props.placeholder || '立即搜尋 IOT'} />
                {props.value !== '' ? (
                  <div className='reset' onClick={this.resetInput}>
                    <i className='icon-close'></i>
                  </div>
                ) : (
                  ''
                )}
              </div>
              <div className='fui-action'>
                <Button onClick={this.doSearch} btnStyle='primary'>
                  搜尋
                </Button>
              </div>
            </div>
          )}
          onSelect={(value, item) => {
            this.setState({ keyword: item });
          }}
          onChange={(event, value) => {
            this.setState({ keywordMenu: [] });
            this.setState({ keyword: value });
            let menu = this.props.defaultKeyword.filter(menu => menu.toLowerCase().indexOf(value.toLowerCase()) > -1);
            this.setState({ keywordMenu: menu });
          }}
          renderMenu={children => <div className='fui-dropdown fui-keyword-menu'>{children}</div>}
          renderItem={(item, isHighlighted) => (
            <div key={`autocompelte-${item}`} className={`fui-item ${isHighlighted ? 'is-selected' : ''}`}>
              <span className='prefix'>
                <i className='icon-search'></i>
              </span>
              <div className='content' dangerouslySetInnerHTML={{ __html: this.highlightKeyword(item) }}></div>
            </div>
          )}
        />
      </div>
    );
  }
}

KeywordInput.propTypes = {
  path: PropTypes.string,
  title: PropTypes.string,
  placeholder: PropTypes.string,
  keyword: PropTypes.string,
  defaultKeyword: PropTypes.arrayOf(PropTypes.string),
};

export default KeywordInput;

```
{% endtab %}
{% endtabs %}

