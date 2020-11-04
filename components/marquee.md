# Marquee

### ESectionMarquee

{% tabs %}
{% tab title="Desktop" %}
![](../.gitbook/assets/image%20%28163%29.png)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/image%20%2816%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Usage" %}
```javascript
import ESectionMarquee from '../components/partials/carousel/ESectionMarquee';

<ESectionMarquee {...AwsMock.corp} />
```
{% endtab %}

{% tab title="Source" %}
```javascript
import React from 'react';
import Marquee from '../../Marquee';
import PropTypes from 'prop-types';

class ESectionMarquee extends React.Component {
    render() {
        return (
            <section className={`fui-corp-content`}>
                <div className="fui-container">
                    <h5 className="mt-0">{this.props.title}</h5>
                    <Marquee direction={'landscape'} loopData={this.props.corps}
                    />
                </div>
            </section>
        )
    }
}

ESectionMarquee.propTypes = {
    title: PropTypes.string,
    corps: PropTypes.arrayOf(
        PropTypes.shape({
            img: PropTypes.string
        })
    )
}

export default ESectionMarquee;
```
{% endtab %}

{% tab title="Mock" %}
```javascript
export const corp = {
  title: '合作過的企業',
  corps: [{ img: '/resources/product/images/corp-logo-1.png' }, { img: '/resources/product/images/corp-logo-2.png' }],
};
```
{% endtab %}
{% endtabs %}

#### Props

| Name | Type | Require | Description |
| :--- | :--- | :--- | :--- |
| title | string |  | 標題 |
| corps | array |  | \[{ img: '/resources/product/images/corp-logo-1.png' }, { img: '/resources/product/images/corp-logo-2.png' }\] |

### ESectionMarquee2

{% tabs %}
{% tab title="Desktop" %}
![](../.gitbook/assets/image%20%28257%29.png)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/image%20%2836%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Usage" %}
```javascript
import ESectionMarquee2 from '../../components/partials/carousel/ESectionMarquee2';

<ESectionMarquee2 {...EbuMedium.corprate} />
```
{% endtab %}

{% tab title="Source" %}
```javascript
import React from 'react';
import Marquee from '../../Marquee';
import ArrowRightWhite from '../../animateArrow/ArrowRightWhite'
import PropTypes from 'prop-types';

class ESectionMarquee2 extends React.Component {
    render() {
        return (
            <section className={`fui-corp-content is-style-2`}>
                <div className="section-bg">
                    <ArrowRightWhite />
                </div>
                <div className="fui-container">
                    <h2 className="mt-0">{this.props.title}</h2>
                    <Marquee direction={'landscape'} loopData={this.props.corps}
                    />
                </div>
            </section>
        )
    }
}

ESectionMarquee2.propTypes = {
    title: PropTypes.string,
    corps: PropTypes.arrayOf(
        PropTypes.shape({
            img: PropTypes.string
        })
    )
}

export default ESectionMarquee2;
```
{% endtab %}

{% tab title="Mock" %}
```javascript
export const corprate = {
  title: "Our corporate partners",
  corps: [
    { img: '/resources/en/logo/att.png' },
    { img: '/resources/en/logo/aws.png' },
    { img: '/resources/en/logo/conexus.png' },
    { img: '/resources/en/logo/microsoft.png' },
    { img: '/resources/en/logo/vodafone.png' },
    { img: '/resources/en/logo/vmware.png' },
  ]
}
```
{% endtab %}
{% endtabs %}

#### Props

| Name | Type | Require | Description |
| :--- | :--- | :--- | :--- |
| title | string |  | 標題 |
| corps | array |  | \[ { img: '/resources/en/logo/att.png' },  { img: '/resources/en/logo/aws.png' }, ...\] |



