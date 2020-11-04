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

| 名稱 | 屬性 | 選項 | 必填 | 說明 |
| :--- | :--- | :--- | :--- | :--- |
| color | string | black \| white |  |  |
| top | number |  |  | container position |
| breadcrumb | array | link: PropTypes.string.isRequired, text: PropTypes.string.isRequired} |  | 麵包屑連結, 麵包屑名稱必填 |



