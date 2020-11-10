# Others

## AnchorDetect

```
import AnchorDetect from '../../components/AnchorDetect';
<AnchorDetect
  className='vertical-anchor-nav'
  items={['anchor0', 'anchor1', 'anchor2', 'anchor3', 'anchor4']}
  activeClass='active'
  offsetTop={145}>
  <li>
    <span>來開箱</span>
  </li>
  <li>
    <span>配件介紹</span>
  </li>
  <li>
    <span>來試用</span>
  </li>
  <li>
    <span>來PK!</span>
  </li>
  <li>
    <span>寫在最後</span>
  </li>
</AnchorDetect>
<OnVisible id='anchor0'>
  anchor0 content
</OnVisible>
```

#### Properties

| 名稱         | 屬性   | 選項 | 必填 | 說明 |
| :----------- | :----- | :--- | :--- | :--- |
| items        | array  |      |      |      |
| itemsName    | array  |      |      |      |
| activeClass  | string |      | true |      |
| offsetTop    | number |      |      |      |
| componentTag | string |      |      |      |
| style        | obj    |      |      |      |
| container    | any    |      |      |      |
| className    | string |      |      |      |
| children     | any    |      |      |      |

---
description: 麵包屑
---

# Breadcrumb

### Breadcrumb

{% tabs %}
{% tab title="First Tab" %}
![](../.gitbook/assets/image%20%28199%29.png)
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Usage" %}
```javascript
import Breadcrumb from '../components/Breadcrumb';

<Breadcrumb breadcrumb={BusinessLoginMock.breadcrumb} />
```
{% endtab %}

{% tab title="Source" %}
```javascript
import React from 'react';
import PropTypes from 'prop-types';

class Breadcrumb extends React.Component {
  overflow = (val) => {
    // console.log(val.length);
    if (val.length > 20) {
      return val.slice(0, 20) + '...'
    } else {
      return val
    }
  }
  render() {
    return (
      <section className='fui-breadcrumb-container' style={{top: this.props.top}}>
        <div className='fui-container'>
          <ul className={`fui-breadcrumb is-${this.props.color}`}>
            {this.props.breadcrumb.map((item, idx) => (
              <li key={`breadcrumb-item-${idx}`}>
                <a href={item.link}>{this.overflow(item.text)}</a>
              </li>
            ))}
          </ul>
        </div>
      </section>
    );
  }
}

Breadcrumb.propTypes = {
  color: PropTypes.string, // black | white
  top: PropTypes.number, // container position
  breadcrumb: PropTypes.arrayOf(
    PropTypes.shape({
      link: PropTypes.string.isRequired, // 麵包屑連結必要
      text: PropTypes.string.isRequired, // 麵包屑名稱必要
    })
  ),
};

export default Breadcrumb;

```
{% endtab %}

{% tab title="Mock" %}
```javascript
export const breadcrumb = [
  { text: '商務首頁', link: '/ebu/index' },
  { text: '企業行動優惠登入', link: '/page/BusinessLogin' },
];
```
{% endtab %}
{% endtabs %}



#### Properties

| 名稱       | 屬性   | 選項                                                                  | 必填 | 說明                       |
| :--------- | :----- | :-------------------------------------------------------------------- | :--- | :------------------------- |
| color      | string | black \| white                                                        |      |                            |
| top        | number |                                                                       |      | container position         |
| breadcrumb | array  | link: PropTypes.string.isRequired, text: PropTypes.string.isRequired} |      | 麵包屑連結, 麵包屑名稱必填 |


## button
* [Button](../elements/button.md)

## CheckModal

```
import CheckModal from '../CheckModal';
<CheckModal open={this.state.modalOpen} closeModal={this.closeModal} submit={this.submit} />
```

#### Properties

| 名稱    | 屬性 | 選項 | 必填 | 說明 |
| :------ | :--- | :--- | :--- | :--- |
| open    | bool |      |      |      |
| content | obj  |      |      |      |
| onClose | func |      |      |      |


## Cookie

```
import Cookie from './components/Cookie';
import Cookie from './components/Cookie';
```

## dropdown

* [Dropdown](../components/dropdown.md)

## Emma

```
import EmmaService from './components/Emma';
const getEmma = () => {
  return {
    text: path.indexOf('/cbu/5g') > -1 ? '我有興趣' : null,
    link: getEmmaLink(),
    show: true,
    useEmmaAvatar: true
  }
}
const getEmmaLink = () => {
  return path.indexOf('/cbu/5g') > -1 ? 'https://enterprise.fetnet.net/content/ebu/tw/5g/form/5G-cbu-form.html' : ''
}
const displayEmma = () => {
  let notDisplayGroup = [
    '/404',
    '/under-maintainance',
    '/ebu/news',
    '/ebu/news/newscontent',
    '/ebu/news/newscontentversion2',
    '/ebu/form/micro-form',
    '/ebu/form/medium-form',
    '/ebu/form/large-form',
    '/ebu/form/public-sector-form',
    '/ebu/form/cloud-form',
    '/ebu/form/smart-wifi-form',
    '/ebu/form/event-form',
    '/ebu/form/5g-form',
    '/ebu/form/5g-event',
    '/ebu/5g',
    '/broadcast',
    '/entrymainframepage',
    '/seednet',
    '/seednet-domain',
    '/office365',
    '/mrtg',
    '/ebu/business-login',
    '/error',
    '/module/section',
  ];
  let result = true;
  for (let i = 0; i < notDisplayGroup.length; i++) {
    if (notDisplayGroup[i] === path.toLowerCase()) {
      result = false
      break
    } else {
      result = true
    }
  }
  // console.log(result);

  return result;
};
<EmmaService {...getEmma()} />
```

#### Properties

| 名稱          | 屬性   | 選項 | 必填 | 說明 |
| :------------ | :----- | :--- | :--- | :--- |
| link          | string |      |      |      |
| useEmmaAvatar | bool   |      |      |      |
| show          | bool   |      |      |      |
| text          | string |      |      |      |


## GoTop
```
import GoTop from './components/GoTop';
<GoTop />
```

## HotWord

```
import HotWord from '../../HotWord';
<HotWord {...{
  path: '/roamingPlan/Apply',
  label: '依地區搜尋',
  // hotword: [
  //   '亞洲',
  //   '美洲',
  //   '歐洲',
  //   '大洋洲',
  //   '中東',
  //   '非洲',
  // ],
  // active: [
  //   true,
  //   false,
  //   false,
  //   false,
  //   false
  // ],
  hotword: [
    { text: '亞洲', active: true },
    { text: '美洲', active: false },
    { text: '歐洲', active: false },
    { text: '大洋洲', active: false },
    { text: '中東', active: false },
    { text: '非洲', active: false },
  ],
}} />
```

#### Properties

| 名稱    | 屬性   | 選項 | 必填 | 說明                                           |
| :------ | :----- | :--- | :--- | :--------------------------------------------- |
| path    | string |      |      |                                                |
| hotword | array  |      |      | text: PropTypes.string,active: PropTypes.bool, |

### KeywordInput

{% tabs %}
{% tab title="Desktop" %}
![](../.gitbook/assets/image%20%28232%29.png)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/image%20%2851%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="First Tab" %}
```javascript
import KeywordInput from '../../KeywordInput';

<KeywordInput
  title={mock.keywordInput}
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

{% tab title="Second Tab" %}
```javascript
import React from 'react';
import Autocomplete from 'react-autocomplete';
import Button from './Button';
import PropTypes from 'prop-types';

class KeywordInput extends React.Component {
  constructor(props) {
    super(props);
    this.input = React.createRef();
    this.state = {
      isEBU: window.location.pathname.indexOf('ebu') > -1,
      keywordMenu: this.props.defaultKeyword.slice(0, 6),
      keyword: this.props.keyword || '',
    };

    this.doSearch = this.doSearch.bind(this);
  }

  componentDidMount() {
    this.setState({
      keyword: this.props.keyword || '',
    });
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

#### Properties

| 名稱           | 屬性   | 必填 | 選項 | 說明           |
| :------------- | :----- | :--- | :--- | :------------- |
| path           | string |      |      | 轉址位置       |
| title          | string |      |      | 標題           |
| placeholder    | string |      |      | 預設顯示       |
| keyword        | string |      |      | 輸入關鍵字     |
| defaultKeyword | array  |      |      | 預設關鍵字陣列 |

## Link

```
import Link from './Link';
<Link
  role='button'
  to="#"
  className='fui-button'>
  content
</Link>
```

### KeywordInput

{% tabs %}
{% tab title="Desktop" %}
![](../.gitbook/assets/image%20%28232%29.png)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/image%20%2851%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="First Tab" %}
```javascript
import KeywordInput from '../../KeywordInput';

<KeywordInput
  title={mock.keywordInput}
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

{% tab title="Second Tab" %}
```javascript
import React from 'react';
import Autocomplete from 'react-autocomplete';
import Button from './Button';
import PropTypes from 'prop-types';

class KeywordInput extends React.Component {
  constructor(props) {
    super(props);
    this.input = React.createRef();
    this.state = {
      isEBU: window.location.pathname.indexOf('ebu') > -1,
      keywordMenu: this.props.defaultKeyword.slice(0, 6),
      keyword: this.props.keyword || '',
    };

    this.doSearch = this.doSearch.bind(this);
  }

  componentDidMount() {
    this.setState({
      keyword: this.props.keyword || '',
    });
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

#### Properties

| 名稱      | 屬性   | 必填 | 選項 | 說明 |
| :-------- | :----- | :--- | :--- | :--- |
| to        | string |      | true |      |
| target    | string |      |      |      |
| className | string |      |      |      |
| children  | node   |      |      |      |

## Loader

```
import Loader from './components/Loader';
<Loader />
```

## Loadmore

components/loadmore.md
* [loadmore](./loadmore.md)

## Marker

```
import Marker from '../Marker'
<Marker
  key={place.id}
  text={place.name}
  lat={place.geometry.location.lat}
  lng={place.geometry.location.lng}
  onClick={() => this.openInfo(place)}
  className={place === this.state.currentStore ? 'active' : ''}
/>
```

## Marquee

```
import Marquee from '../../Marquee';
const marqueeData = props.list.reduce((accumulator, value, index, array) => {
    accumulator.push({ img: value.logo });
    return accumulator;
  }, []);
<Marquee direction={'landscape'} loopData={marqueeData} />
```

#### Properties

| 名稱               | 屬性   | 選項 | 必填 | 說明                                                                                              |
| :----------------- | :----- | :--- | :--- | :------------------------------------------------------------------------------------------------ |
| loop               | bool   |      |      |                                                                                                   |
| loopData           | array  |      | true | retinaImg: PropTypes.string,img: PropTypes.string,height: PropTypes.string,txt: PropTypes.string, |
| getMarquee         | func   |      |      |                                                                                                   |
| direction          | string |      | true |                                                                                                   |
| verticalItemHeight | string |      |      |                                                                                                   |


## Menu

```
import Menu from './Menu';
<Menu
  id={this.props.id}
  anchorEl={this.state.anchorEl}
  keepMounted
  open={Boolean(this.state.anchorEl)}
  onClose={this.readyToClose}>
  <div className='menu-wrapper'>
    {this.props.list.map((item, idx) =>
      Array.isArray(item) ? (
        item.length > 0 && (
          <div className='fui-menu-group' key={'menu-item-group-' + idx + this.props.id}>
            {item.map((it, i) => (
              <Item
                {...it}
                className={`${
                  (this.props.selected && this.props.selected === it.text) ||
                    (!this.props.selected &&
                      (this.state.selectedItem === it.text ||
                        (this.props.value && this.props.value === it.value)))
                    ? 'active'
                    : ''
                  } ${this.props.hasCheck ? 'check-icon' : ''}`}
                key={'menu-item' + idx + this.props.id + i}
                onClick={(e) => this.selectItem(it, idx, e)}>
                {it.text}
              </Item>
            ))}
          </div>
        )
      ) : (
          <Item
            {...item}
            className={`${
              (this.props.selected && this.props.selected === item.text) ||
                (!this.props.selected &&
                  (this.state.selectedItem === item.text || (this.props.value && this.props.value === item.value)))
                ? 'active'
                : ''
              } ${this.props.hasCheck ? 'check-icon' : ''} ${this.getSelected(item)}`}
            key={'menu-item' + this.props.id + idx}
            onClick={(e) => this.selectItem(item, idx, e)}>
            {item.text}
          </Item>
        )
    )}
  </div>
</Menu>
```

#### Properties

| 名稱      | 屬性   | 選項 | 必填 | 說明 |
| :-------- | :----- | :--- | :--- | :--- |
| id        | string |      |      |      |
| anchorEl  | obj    |      |      |      |
| className | string |      |      |      |
| children  | any    |      | true |      |
| onClose   | func   |      |      |      |


## Notification

```
import NotificationBar from '../../Notification';
<NotificationBar
  onLoad={(e) => {
    notibarLoad();
  }}
  className='image-bulletin'
  image={{
    appIcon: '',
    md: '/resources/cbu/cbu-index/img-splash-promo@2x.jpg',
    sm: '/resources/cbu/cbu-index/img-splash-promo.jpg',
    alt: '廣告圖',
  }}
  appText=''
  count={5}
  activityName='小米促銷活動'
  link=''
  type='image-bulletin'
  title='小米體重計2只要 $399'
  click={2}
  second={5}
  target='_blank'
  activityDsc=''
  appDesc=''
  btn='查看詳情'
  sound={true}
/>
```

#### Properties

| 名稱            | 屬性   | 選項 | 必填 | 說明 |
| :-------------- | :----- | :--- | :--- | :--- |
| className       | string |      |      |      |
| message         | string |      |      |      |
| closeIconStyles | obj    |      |      |      |
| sound           | bool   |      |      |      |


## ProgressBar

```
import ProgressBar from '../../components/ProgressBar';
<ProgressBar progress={60} bold={true} color='red' />
```

#### Properties

| 名稱     | 屬性   | 選項 | 必填 | 說明         |
| :------- | :----- | :--- | :--- | :----------- |
| progress | number |      |      |              |
| color    | string |      |      | red  or blue |
| bold     | bool   |      |      |              |

## SearchBoxList

```
import SearchBoxList from '../../components/SearchBoxList';
<SearchBoxList 
  match={this.props.match}
  tab={this.state.currentTab}
  location={this.props.location}
  history={this.props.history}
  searchList={this.state.searchList} 
/>
```

## SelectedArticle

```
import SelectedArticle from '../../components/SelectedArticle';
<SelectedArticle article={[
    {
      id: 'link_01',
      content: 'Dyson TP06智慧空氣清淨機 消除甲醛 為家中長輩、小孩帶來室內清新好空氣',
      link: '#',
    },
    {
      id: 'link_02',
      content: '今天起就讓LG WiFi濕拖清潔機器人幫你做家事！ LG CordZero...',
      link: '#',
    },
    {
      id: 'link_03',
      content: '簡單生活之居家空間三要素，下一個居家IG網紅就是你',
      link: '#',
    },
    {
      id: 'link_04',
      content: '恆壓電控水箱的石頭 S5 Max',
      link: '#',
    },
    {
      id: 'link_05',
      content: '麗克特微笑鬆餅機 | Recolte Smile Baker RSM-1 在家自製鬆餅，好吃又...',
      link: '#',
    },
    {
      id: 'link_06',
      content: '[開箱] 夏天這麼長，風扇更不能隨便！Stadler Form 完整你對夏天的涼爽想像',
      link: '#',
    },
  ]} title='人氣文章' />
```

#### Properties

| 名稱    | 屬性   | 選項 | 必填 | 說明 |
| :------ | :----- | :--- | :--- | :--- |
| title   | string |      |      |      |
| article | array  |      |      |      |


## SingleVideo

```
import SingleVideo from '../../components/SingleVideo';
<SingleVideo
  videoId='9FaXQK51iM8'
  imgSmall='/resources/cbu/img/video-02.jpg'
  imgLarge='/resources/cbu/img/video-02.jpg'
  videoLink='df-gMDkuC08'
  alterVideo={null}
/>
```
#### Properties

| 名稱       | 屬性   | 選項 | 必填 | 說明 |
| :--------- | :----- | :--- | :--- | :--- |
| title      | string |      |      |      |
| videoId    | string |      |      |      |
| imgLarge   | string |      |      |      |
| imgSmall   | string |      |      |      |
| videoLink  | string |      |      |      |
| alterVideo | string |      |      |      |


## SocialMedia
```
import SocialMedia from '../../components/SocialMedia';
<SocialMedia
  theme="light"
  fbLink="#"
  lineLink="#"
  size={48}
  displayContent="分享遠傳優惠"
/>
```

#### Properties

| 名稱           | 屬性   | 選項 | 必填 | 說明 |
| :------------- | :----- | :--- | :--- | :--- |
| fbLink         | string |      |      |      |
| lineLink       | string |      |      |      |
| displayContent | string |      |      |      |
| size           | number |      |      |      |
| theme          | string |      |      |      |


## switch

```
import Switch from '../../Switch';
<Switch
  on='開啟'
  off='關閉'
  name='type'
  checked={form.type.value}
  onChange={(e, checked) => this.inputChange('type', checked)}
/>
```
#### Properties

| 名稱     | 屬性   | 選項 | 必填 | 說明 |
| :------- | :----- | :--- | :--- | :--- |
| checked  | bool   |      |      |      |
| name     | string |      | true |      |
| on       | string |      | true |      |
| off      | string |      | true |      |
| onChange | func   |      |      |      |

## tableBtnModal

```
import Modal from '../../components/tableBtnModal';
<Modal open={this.state.openModal} detailContent={this.state.detailContent} onClose={this.closeModal} />
```
#### Properties

| 名稱          | 屬性 | 選項 | 必填 | 說明 |
| :------------ | :--- | :--- | :--- | :--- |
| open          | bool |      |      |      |
| detailContent | obj  |      |      |      |
| onClose       | func |      |      |      |

## Tooltip

```
import Tooltip from '../../components/Tooltip';
<Tooltip
  parentNode={null}
  content={<i className='icon-information'></i>}
  trigger="click"
  tooltip={card.tooltip} />
```

#### Properties

| 名稱       | 屬性   | 選項 | 必填 | 說明 |
| :--------- | :----- | :--- | :--- | :--- |
| parentNode | obj    |      |      |      |
| content    | node   |      |      |      |
| trigger    | string |      |      |      |
| tooltip    | string |      |      |      |
| className  | string |      |      |      |
| onOpen     | func   |      |      |      |
| position   | string |      |      |      |


## VideoCarousel

```
import VideoCarousel from '../../components/VideoCarousel';
<VideoCarousel
  title="達人帶你玩"
  videos={[
    {
      videoId: '9FaXQK51iM8',
      title: '關西賞櫻超夯打卡景點',
      content: '日本 5 天遠遊卡只要 $199',
      imgSmall: '/resources/cbu/roaming/i-stock-970064046.jpg',
      imgLarge: '/resources/cbu/roaming/i-stock-970064046.jpg',
      videoLink: 'https://youtu.be/u9YYwJKQ0aQ',
      alterVideo: null,
    },
    {
      videoId: '9FaXQK51iM8',
      title: '關西賞櫻超夯打卡景點22',
      content: '日本 5 天遠遊卡只要 $199',
      imgSmall: '/resources/cbu/roaming/i-stock-970064046.jpg',
      imgLarge: '/resources/cbu/roaming/i-stock-970064046.jpg',
      videoLink: 'https://youtu.be/u9YYwJKQ0aQ',
      alterVideo: null,
    },
    {
      videoId: '9FaXQK51iM8',
      title: '關西賞櫻超夯打卡景點33',
      content: '日本 5 天遠遊卡只要 $199',
      imgSmall: '/resources/cbu/roaming/i-stock-970064046.jpg',
      imgLarge: '/resources/cbu/roaming/i-stock-970064046.jpg',
      videoLink: 'https://youtu.be/CwfE29SgSZE',
      alterVideo: 'http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/ElephantsDream.mp4',
    }
  ]}
/>
```

#### Properties

| 名稱      | 屬性   | 選項 | 必填 | 說明                                                                                                                                                           |
| :-------- | :----- | :--- | :--- | :------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| className | string |      |      |                                                                                                                                                                |
| title     | string |      |      |                                                                                                                                                                |
| videos    | array  |      | true | videoId: PropTypes.string,title: PropTypes.string,content: PropTypes.string,imgSmall: PropTypes.string,imgLarge: PropTypes.string,alterVideo: PropTypes.string |


## VideoModal

```
import VideoModal from './VideoModal';
openVideoModal = (data) => {
    this.setState({
      modalOpen: true,
      alterVideo: data.alterVideo ? data.alterVideo : null,
      currentVideo: data.videoId,
    });
  };

  closeModal = () => {
    this.setState({
      modalOpen: false,
      alterVideo: '',
      currentVideo: '',
    });
  };
<VideoModal
  open={this.state.modalOpen}
  alterVideo={this.state.alterVideo}
  videoUrl={this.state.currentVideo}
  onClose={this.closeModal}
/>
```

#### Properties

| 名稱       | 屬性   | 選項 | 必填 | 說明 |
| :--------- | :----- | :--- | :--- | :--- |
| open       | bool   |      | true |      |
| videoUrl   | string |      |      |      |
| alterVideo | string |      |      |      |
| onClose    | func   |      | true |      |
