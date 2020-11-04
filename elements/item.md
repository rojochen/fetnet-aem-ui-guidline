# Item

用於一般條例項目，可帶圖片或 icon，也可帶入 className 做客製化調整

{% tabs %}
{% tab title="Usage" %}
```jsx
import Item from '../components/Item';

<Item>{Text}</Item>

// 與 <Menu> 共用
import Menu from '../components/Menu';
import Item from '../components/Item';


const Dropdown = (props) => {
	const selectItem = (item, idx) => {
	    props.onChange(item)
	    closeMenu()
	}
	
	let renderMenuItem = props.data.map((item, idx) => <Item key={'menu-item' + props.id + idx} onClick={e => selectItem(item, idx)}>{item}</Item>)
	return (
		<Menu>
		    {renderMenuItem}
		</Menu>
	)
}
```
{% endtab %}

{% tab title="Item.js" %}
```jsx
import React from 'react';
import PropTypes from 'prop-types';

const Item = (props) => {
    const renderPrefix = (prefix) => {
        if(!prefix) return '';

        switch (prefix) {
            case 'check':
                return <span className="prefix"><i className="icon-check"></i></span>;
                
            case 'bulleted':
                return <span className="prefix"><i className="bulleted-dot"></i></span>;
                
            case 'number':
                return <span className="prefix"><i className="number">{props.number}</i></span>;
                
            default: 
                return '';
        }
    }

    return (
        <div className={`fui-item ${props.className ? props.className : ''} ${props.disabled ? 'is-disabled' : ''}`}>
            {
                props.img 
                ? <img src={props.img} alt={props.children} />
                : ""
            }
            {renderPrefix(props.prefix)}
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

Item.propTypes = {
    className: PropTypes.string,
    number: PropTypes.number, // if prefix === number, auto use in map
    prefix: PropTypes.string, // check | bulleted | number
    icon: PropTypes.string,
    children: PropTypes.string.isRequired,
    img: PropTypes.string
}

export default Item;
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
      <td style="text-align:left">img</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x6587;&#x5B57;&#x524D;&#x65B9;&#x53EF;&#x5E36;&#x5C0F;&#x5716;&#x7247;&#xFF0C;&#x4E0D;&#x8A2D;&#x5B9A;&#x5247;&#x4E0D;&#x986F;&#x793A;</td>
    </tr>
    <tr>
      <td style="text-align:left">number</td>
      <td style="text-align:left">Number</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x5982;&#x679C; <code>prefix </code>&#x70BA;<code> number</code>&#xFF0C;&#x5247;&#x53EF;&#x4EE5;&#x5E36;&#x5165;&#x6578;&#x5B57;&#x3002;</td>
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

