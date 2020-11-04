---
description: 為頁面上有特別標示可導入到其他頁面的功能，連結根據所在位置不同會具備不同的樣式，以下列出幾種連接樣式的規範。
---

# Link

## TextLink - L

Hover動效: 文字範圍底部伸縮2px底線CSS緩動方式: 300ms, ease-in-out

<table>
  <thead>
    <tr>
      <th style="text-align:left"></th>
      <th style="text-align:left"></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p>
          <img src="../.gitbook/assets/web-tectliink-l.png" alt/>
        </p>
        <p>Default</p>
      </td>
      <td style="text-align:left">
        <p>
          <img src="../.gitbook/assets/web-textlink-l-hover.png" alt/>
        </p>
        <p>Hover</p>
      </td>
    </tr>
  </tbody>
</table>

#### Code

具備連結功能的標題，可以導入網站主頁。在網頁內容中的 Panel 中，使用連結包入 &lt;h4/&gt;。

{% tabs %}
{% tab title="React" %}
```jsx
import { Link } from 'react-route-dom';
import Panel from '../components/panel/Panel';

<Panel>
    <Link to="/your/link" className="sub-link-title">
        <h4>Your Link Text</h4>
    </Link>
</Panel>
```
{% endtab %}
{% endtabs %}

[DEMO](http://fetnet-storybook.aja.com.tw/iframe.html?id=link--text-link-large) 

## Textlink - M

Hover動效: 文字範圍底部伸縮2px底線CSS緩動方式: 300ms, ease-in-out

<table>
  <thead>
    <tr>
      <th style="text-align:left">EBU</th>
      <th style="text-align:left"></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p>
          <img src="../.gitbook/assets/ebu-textlink-m (1).png" alt/>
        </p>
        <p>Default</p>
      </td>
      <td style="text-align:left">
        <p>
          <img src="../.gitbook/assets/textlink-m-press.png" alt/>
        </p>
        <p>Hover</p>
      </td>
    </tr>
  </tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">CBU</th>
      <th style="text-align:left"></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p>
          <img src="../.gitbook/assets/cbu-textlink-m.png" alt/>
        </p>
        <p>Default</p>
      </td>
      <td style="text-align:left">
        <p>
          <img src="../.gitbook/assets/cbu-textlink-m-press.png" alt/>
        </p>
        <p>Hover</p>
      </td>
    </tr>
  </tbody>
</table>

#### Code

在頁面一般內容中使用。

{% tabs %}
{% tab title="React" %}
```jsx
import { Link } from 'react-route-dom';


<Link to="/your/link">
    Your Link Text
</Link>
```
{% endtab %}
{% endtabs %}

[DEMO](http://fetnet-storybook.aja.com.tw/iframe.html?id=link--text-link-medium)

## Menulink

Hover動效: 文字顏色漸變CSS緩動方式: 300ms, ease-in-out

<table>
  <thead>
    <tr>
      <th style="text-align:left">CBU</th>
      <th style="text-align:left"></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p>
          <img src="../.gitbook/assets/textlink_menu_s.png" alt/>
        </p>
        <p>Default</p>
      </td>
      <td style="text-align:left">
        <p>
          <img src="../.gitbook/assets/textlink_menu-cbu.png" alt/>
        </p>
        <p>Hover</p>
      </td>
    </tr>
  </tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">EBU</th>
      <th style="text-align:left"></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p>
          <img src="../.gitbook/assets/textlink_menu_s.png" alt/>
        </p>
        <p>Default</p>
      </td>
      <td style="text-align:left">
        <p>
          <img src="../.gitbook/assets/textlink_menu-cbu-1-.png" alt/>
        </p>
        <p>Hover</p>
      </td>
    </tr>
  </tbody>
</table>

#### Code

在 header 中，分為側邊欄，子選項等不同樣式。

{% tabs %}
{% tab title="React" %}
```jsx
import { Link } from 'react-route-dom';
import LinkItem from '../../item/LinkItem';

<header>
    <Link to="/your/link">
        <h4>Your Link Text</h4>
    </Link>
    <LinkItem link={"/link/to/your/path"}>
        Your Link Text
    </LinkItem>
<header>
```
{% endtab %}
{% endtabs %}

[DEMO](http://fetnet-storybook.aja.com.tw/iframe.html?id=link--menu-link)

## Footer Textlink

Hover動效：整體淡化 \(透明度 60%\)CSS緩動方式: 300ms, ease-in-out

![](../.gitbook/assets/footer-textlink-hover%20%281%29.png)

<table>
  <thead>
    <tr>
      <th style="text-align:left"></th>
      <th style="text-align:left"></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p>
          <img src="../.gitbook/assets/footer-textlink.png" alt/>
        </p>
        <p>Default</p>
      </td>
      <td style="text-align:left">
        <p>
          <img src="../.gitbook/assets/footer-textlink-hover (1).png" alt/>
        </p>
        <p>Hover</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p>
          <img src="../.gitbook/assets/footer-textlink-dark-1-.png" alt/>
        </p>
        <p>Default &#x6DF1;&#x8272;&#x5E95;</p>
      </td>
      <td style="text-align:left">
        <p>
          <img src="../.gitbook/assets/footer-textlink-dark.png" alt/>
        </p>
        <p>Hover &#x6DF1;&#x8272;&#x5E95;</p>
      </td>
    </tr>
  </tbody>
</table>

#### Code

{% tabs %}
{% tab title="React" %}
```jsx
import { Link } from 'react-route-dom';
import LinkItem from '../../item/LinkItem';

<footer>
    <Link to="/your/link">
        <h4>Your Link Text</h4>
    </Link>
</footer>
```
{% endtab %}
{% endtabs %}

[DEMO](http://fetnet-storybook.aja.com.tw/iframe.html?id=link--footer-link)

