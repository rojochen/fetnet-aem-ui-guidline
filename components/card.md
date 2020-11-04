# Card

牌卡以 `<Card />` 為單位，依設計搭配不同的 section 或樣式名稱。

也可以直接使用 HTML 依照架構放入內容。若有不需要的欄位，可不帶參數或不使用該 HTML。



{% tabs %}
{% tab title="Usage" %}
```jsx

import Card from '../components/card/Card';

<Card
    className="promotion-article"
    link={'#'}
    icon='/resources/help-center/images/business-response.svg'
    title='企業用戶問題反應'
    description='有任何問題嗎? 您可立即線上填寫資料，預約專人為您服務。'
/>
```
{% endtab %}

{% tab title="Card.js" %}
```jsx
import React from 'react';
import { Link } from 'react-router-dom'
import PropTypes from 'prop-types';

const Card = props => {
    const renderCardContent = () => {
        return props.link ? (
            <Link className='fui-card-action' to={props.link}>
                {
                    props.image ? (
                        <div className="fui-card-image">
                            <img src={props.image} srcSet={props.retinaImage || props.image} alt={props.meta} />
                        </div>
                    ) : ''
                }
                <div className='fui-card-caption'>
                    <div className='fui-card-content'>
                        {
                            (!props.public_at) ? '' : (
                                <div className="fui-card-date">{props.public_at}</div>
                            )
                        }
                        {
                            (!props.meta) ? '' : (
                                <div className="fui-card-meta">{props.meta}</div>
                            )
                        }
                        <h4 className="fui-card-title">
                            {
                                (!props.icon) ? '' : (
                                    <div className='icon'>
                                        <img src={props.icon} alt={props.meta} />
                                    </div>
                                )
                            }
                            <div className='text'>
                                {props.title}
                            </div>
                        </h4>
                        {
                            (!props.description) ? '' : (
                                <p className="fui-card-description" dangerouslySetInnerHTML={{ __html: props.description }}>
                                </p>
                            )
                        }
                    </div>
                    <div className='fui-card-extra'>
                        <div className={`fui-button is-arrow mb-0 ${props.className && props.className.indexOf('promotion-article') > -1 ? 'is-reverse' : ''}`}>
                            {props.action ? props.action.text : '看更多'}
                        </div>
                    </div>
                </div>
            </Link>
        ) : (
                <div className="fui-card-action">
                    {
                        props.image ? (
                            <div className="fui-card-image">
                                <img src={props.image} srcSet={props.retinaImage || props.image} alt={props.meta} />
                            </div>
                        ) : ''
                    }
                    <div className='fui-card-caption'>
                        <div className='fui-card-content'>
                            {
                                (!props.public_at) ? '' : (
                                    <div className="fui-card-date">{props.public_at}</div>
                                )
                            }
                            {
                                (!props.meta) ? '' : (
                                    <div className="fui-card-meta">{props.meta}</div>
                                )
                            }
                            <h4 className="fui-card-title">
                                {
                                    (!props.icon) ? '' : (
                                        <div className='icon'>
                                            <img src={props.icon} alt={props.meta} />
                                        </div>
                                    )
                                }
                                {props.title}
                            </h4>
                            {
                                (!props.description) ? '' : (
                                    <p className="fui-card-description" dangerouslySetInnerHTML={{ __html: props.description }}>
                                    </p>
                                )
                            }
                        </div>
                        <div className='fui-card-extra'>
                            <div className={`fui-button is-arrow mb-0 ${props.className && props.className.indexOf('promotion-article') > -1 ? 'is-reverse' : ''}`}>
                                {props.action ? props.action.text : '看更多'}
                            </div>
                        </div>
                    </div>
                </div>
            )
    }

    return (
        <div className={`fui-card ${props.className ? props.className : ''}`}>
            {renderCardContent()}
        </div>
    )
}

Card.propTypes = {
    className: PropTypes.string,
    link: PropTypes.string,
    retinaImage: PropTypes.string,
    image: PropTypes.string,
    meta: PropTypes.string,
    icon: PropTypes.string,
    public_at: PropTypes.string,
    title: PropTypes.string.isRequired,
    description: PropTypes.string,
    action: PropTypes.shape({
        text: PropTypes.string.isRequired,
        link: PropTypes.string
    })
};

export default Card;
```
{% endtab %}

{% tab title="card.html" %}
```markup
<!-- 整張牌卡都可點擊 -->
<div class='fui-card'>
    <a href="#" class="fui-card-action">
        <div class="fui-card-image">
            <img src="..." srcSet="..." alt="..." />
        </div>
        <div class='fui-card-caption'>
            <div class='fui-card-content'>
                <div class="fui-card-meta">...</div>
                <h4 class="fui-card-title">
                    <div class='icon'>
                        <img src="" alt="" />
                    </div>
                    Title
                </h4>
                <p className="fui-card-description">
                    ...
                </p>
            </div>
            <div class='fui-card-extra'>
                <div class='fui-button is-arrow mb-0'>
                    看更多
                </div>
            </div>
        </div>
    </a>
</div>


<!-- 部分可點擊 -->
<div class='fui-card'>
    <div class="fui-card-action">
        <div class="fui-card-image">
            <img src="..." srcSet="..." alt="..." />
        </div>
        <div class='fui-card-caption'>
            <div class='fui-card-content'>
                <div class="fui-card-meta">...</div>
                <h4 class="fui-card-title">
                    <div class='icon'>
                        <img src="" alt="" />
                    </div>
                    Title
                </h4>
                <p className="fui-card-description">
                    ...
                    <a href="#">...</a>
                </p>
            </div>
            <div class='fui-card-extra'>
                <a href="#" class='fui-button is-arrow mb-0'>
                    看更多
                </a>
            </div>
        </div>
    </div>
</div>
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
      <th style="text-align:left">&#x5FC5;&#x586B;</th>
      <th style="text-align:left">&#x8AAA;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">className</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        <p><code>is-document</code> 
          <br /><code>is-price-card</code> 
          <br /><code>is-simple</code> 
          <br /><code>is-tooltip</code> 
          <br /><code>service-entry</code> 
          <br /><code>box</code> 
          <br /><code>promotion-article </code>
        </p>
        <p><code>is-video</code>
        </p>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x53EF;&#x4F7F;&#x7528;&#x7684;&#x6A23;&#x5F0F;&#x540D;&#x7A31;&#xFF0C;&#x4F46;&#x9700;&#x642D;&#x914D;
        <a
        href="https://app.gitbook.com/@ajacreative/s/fetnet-1/~/drafts/-M15BRlqEZqvK-93qDf7/sections/card">section</a>&#x4F7F;&#x7528;</td>
    </tr>
    <tr>
      <td style="text-align:left">link</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x8981;&#x5C0E;&#x5165;&#x7684;&#x9023;&#x7D50;</td>
    </tr>
    <tr>
      <td style="text-align:left">image</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x724C;&#x5361;&#x5716;&#x7247;</td>
    </tr>
    <tr>
      <td style="text-align:left">retinaImage</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x5728; retina display &#x4E2D;&#x986F;&#x793A;&#x7684;&#x5716;&#x7247;</td>
    </tr>
    <tr>
      <td style="text-align:left">meta</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x5C0F;&#x6A19;</td>
    </tr>
    <tr>
      <td style="text-align:left">title</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">true</td>
      <td style="text-align:left">&#x6A19;&#x984C;</td>
    </tr>
    <tr>
      <td style="text-align:left">icon</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x6A19;&#x984C;&#x4E0A;&#x7684; icon</td>
    </tr>
    <tr>
      <td style="text-align:left">public_at</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x65E5;&#x671F;</td>
    </tr>
    <tr>
      <td style="text-align:left">description</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x63CF;&#x8FF0;</td>
    </tr>
    <tr>
      <td style="text-align:left">action</td>
      <td style="text-align:left">Object</td>
      <td style="text-align:left">
        <p>text: String</p>
        <p>link: String</p>
      </td>
      <td style="text-align:left">&#x82E5;&#x6709;&#x4F7F;&#x7528; action&#xFF0C;text &#x70BA;&#x5FC5;&#x586B;</td>
      <td
      style="text-align:left">&#x724C;&#x5361;&#x4E0A;&#x6309;&#x9215;</td>
    </tr>
  </tbody>
</table>



