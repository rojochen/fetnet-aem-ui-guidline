# SocailMedia

### SocailMedia

{% tabs %}
{% tab title="Usage" %}
```javascript
import SocialMedia from '../components/SocialMedia';

<SocialMedia
    theme="light"
    fbLink="#"
    lineLink="#"
    size={48}
    displayContent="分享遠傳優惠"
/>
```
{% endtab %}

{% tab title="Source" %}
```javascript
import React, { Component } from 'react';
import Link from './Link';
import PropTypes from 'prop-types';

class SocialMedia extends Component {
  constructor(props) {
    super(props);
    console.log(this.props);
  }

  linkFormat(link) {
    let linkString =
      link.indexOf('//') > -1 ? link : typeof window !== 'undefined' ? window.location.origin : '' + link;

    return encodeURIComponent(linkString);
  }

  render() {
    return (
      <div className={`social-media d-flex flex-align-center ${this.props.theme ? 'is-' + this.props.theme : ''}`}>
        <div
          className='d-inline-block mr-2'
          dangerouslySetInnerHTML={{
            __html: this.props.displayContent,
          }}></div>
        {!!this.props.lineLink ? (
          <Link
            to={`//social-plugins.line.me/lineit/share?url=${this.linkFormat(this.props.lineLink)}`}
            target='_blank'>
            <i style={!!this.props.size ? { fontSize: this.props.size } : null} className={`icon-line-sm`}></i>
          </Link>
        ) : null}
        {!!this.props.fbLink ? (
          <Link to={`//www.facebook.com/sharer.php?u=${this.linkFormat(this.props.fbLink)}`} target='_blank'>
            <i style={!!this.props.size ? { fontSize: this.props.size } : null} className={`icon-facebook-sm`}></i>
          </Link>
        ) : null}
      </div>
    );
  }
}

SocialMedia.propTypes = {
  fbLink: PropTypes.string,
  lineLink: PropTypes.string,
  displayContent: PropTypes.string,
  size: PropTypes.number,
  theme: PropTypes.string,
};

export default SocialMedia;

```
{% endtab %}
{% endtabs %}

![](../.gitbook/assets/image%20%2893%29.png)

#### Properties

| 名稱 | 屬性 | 選項 | 說明 |
| :--- | :--- | :--- | :--- |
| fbLink | string |  | fb連結 |
| lineLink | string |  | line連結 |
| displayContent | string |  | 內容 |
| size | number | 42 | 字級大小 |
| theme | string | dark/light | 佈景色 |

