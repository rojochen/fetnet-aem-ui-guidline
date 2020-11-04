# LinkItem

與 Item 類似，多了 Link 效果。

{% tabs %}
{% tab title="Usage" %}
```jsx

import LinkItem from '../../item/LinkItem';

<LinkItem link={'path/you/want/to/guide'} className='item'>
  {item.text}
</LinkItem>

// 文字前加上圖片
<LinkItem link={'path/you/want/to/guide'} img={'/resources/common/images/global.png'}>
  English
</LinkItem>
```
{% endtab %}

{% tab title="LinkItem.js" %}
```jsx
import React from 'react';
import PropTypes from 'prop-types';

const LinkItem = (props) => {
    const handleClick = (e) => {
        e.preventDefault();
        if (props.link) {
            if (props.target === '_blank')
                window.open(props.link)
            else {
                if (props.link.indexOf('#')===0) {
                    window.location.hash = props.link
                } else 
                    window.location.href = props.link
            }
        } else {
            if(props.onClick) props.onClick()
        }
    }

    return (
        <div
        role={props.link || props.onClick ? 'button' : ''}
        onClick={handleClick}
        className={`fui-item ${props.className ? props.className : ''}`}>
            {
                props.img 
                ? <img src={props.img} alt={props.children} />
                : ""
            }
            {
                props.prefixIcon 
                ? <span className='prefix'>
                    <i className={`icon-${props.prefixIcon}`}></i>
                  </span>
                : ''
            }
            <span className='content'>{props.children}</span>
            {
                props.icon 
                ? <span className='extra'>
                    <i className={`icon-${props.icon}`}></i>
                  </span>
                : ''
            }
        </div>
    );
}

LinkItem.propTypes = {
    className: PropTypes.string,
    link: PropTypes.string,
    number: PropTypes.number,
    prefix: PropTypes.string,
    icon: PropTypes.string,
    children: PropTypes.string.isRequired,
    img: PropTypes.string,
    target: PropTypes.string,
    onClick: PropTypes.func
}

export default LinkItem;
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
      <td style="text-align:left">children</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>&#x6587;&#x5B57;&#x5167;&#x5BB9;&#xFF0C;&#x76F4;&#x63A5;&#x653E;&#x5728;&#x6A19;&#x7C64;&#x4E2D;</p>
        <p><code>&lt;Item&gt;{&apos;&#x9078;&#x9805; 1&apos;}&lt;/Item&gt;</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">prefix</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"><code>check</code>  <code>bulleted</code>  <code>number</code>
      </td>
      <td style="text-align:left">Item &#x524D;&#x7F6E;&#x5716;&#x6A23;&#xFF0C;&#x82E5;&#x4E0D;&#x8A2D;&#x5B9A;&#x5247;&#x4E0D;&#x986F;&#x793A;</td>
    </tr>
    <tr>
      <td style="text-align:left">number</td>
      <td style="text-align:left">Number</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x5982;&#x679C; <code>prefix </code>&#x70BA;<code> number</code>&#xFF0C;&#x5247;&#x53EF;&#x4EE5;&#x5E36;&#x5165;&#x6578;&#x5B57;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">img</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x6587;&#x5B57;&#x524D;&#x65B9;&#x53EF;&#x5E36;&#x5C0F;&#x5716;&#x7247;&#xFF0C;&#x4E0D;&#x8A2D;&#x5B9A;&#x5247;&#x4E0D;&#x986F;&#x793A;</td>
    </tr>
    <tr>
      <td style="text-align:left">icon</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">Item &#x5F8C;&#x65B9;&#x53EF;&#x5E36; icon&#xFF0C;&#x4E0D;&#x8A2D;&#x5B9A;&#x5247;&#x4E0D;&#x986F;</td>
    </tr>
    <tr>
      <td style="text-align:left">onClick</td>
      <td style="text-align:left">Function</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x53EF;&#x4EE5;&#x8A2D;&#x5B9A;&#x9EDE;&#x64CA;&#x5F8C;&#x7684;&#x4E92;&#x52D5;&#x4E8B;&#x4EF6;</td>
    </tr>
    <tr>
      <td style="text-align:left">link</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x8981;&#x6307;&#x5411;&#x7684;&#x9023;&#x7D50;</td>
    </tr>
    <tr>
      <td style="text-align:left">target</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"><code>_self</code><em>  <code>_blank</code></em>
      </td>
      <td style="text-align:left">&#x9023;&#x7D50;&#x5C0E;&#x5411;&#x65B9;&#x5F0F;&#xFF0C;&#x9810;&#x8A2D;&#x70BA; <code>self</code><em>&#xFF0C;</em><code>_blank</code><em> &#x70BA;&#x53E6;&#x958B;&#x8996;&#x7A97;</em>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">ClassName</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left"><code>paded</code> &#x9593;&#x8DDD;&#x52A0;&#x5927;
        <br /><code>is-underline</code> &#x6587;&#x5B57;&#x6709;&#x5E95;&#x7DDA;
        <br /><code>text-sm</code> &#x6587;&#x5B57;&#x8F03;&#x5C0F;
        <br /><code>is-active </code>&#x88AB;&#x9078;&#x64C7;&#x72C0;&#x614B;</td>
      <td
      style="text-align:left">&#x4F7F;&#x7528; &lt;Item/&gt; &#x53EF;&#x5E36;&#x5165;&#x6240;&#x9700;&#x8981;&#x7684;&#x6A23;&#x5F0F;&#x540D;&#x7A31;&#x5BA2;&#x88FD;&#x5316;</td>
    </tr>
  </tbody>
</table>

