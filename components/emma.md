# Emma

<table>
  <thead>
    <tr>
      <th style="text-align:left">EBU</th>
      <th style="text-align:left">CBU</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p></p>
        <p>
          <img src="../.gitbook/assets/jie-tu-20200304-xia-wu-3.17.17.png" alt/>
        </p>
      </td>
      <td style="text-align:left">
        <p></p>
        <p>
          <img src="../.gitbook/assets/jie-tu-20200304-xia-wu-3.21.03.png" alt/>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p></p>
        <p>
          <img src="../.gitbook/assets/jie-tu-20200304-xia-wu-3.17.34.png" alt/>
        </p>
      </td>
      <td style="text-align:left">
        <p></p>
        <p>
          <img src="../.gitbook/assets/jie-tu-20200304-xia-wu-3.18.01.png" alt/>
        </p>
      </td>
    </tr>
  </tbody>
</table>

{% tabs %}
{% tab title="" %}
```jsx
import EmmaService from './components/Emma';

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
      if (notDisplayGroup[i] == path.toLowerCase()) {
        result = false
        break
      } else {
        result = true
      }
    }
    return result;
  };


<EmmaService show={displayEmma()} />
```
{% endtab %}

{% tab title="Emma.js" %}
```jsx
import React from 'react';
import { withRouter } from 'react-router-dom';
import PropTypes from 'prop-types';

class EmmaService extends React.Component {
  constructor(props) {
    // console.log(`props`, props);
    super(props);
    this.state = {
      isEbu: this.props.location.pathname.indexOf('/ebu') > -1,
      isHelpCenter: this.props.location.pathname.indexOf('/help-center') > -1,
      fixBottom: 24,
      distance: window.innerWidth < 960 ? 72 : 76,
    };
    this.emma = React.createRef();
    this.clearTimeout = false;
    this.openTimeout = false;
  }

  setPosition = () => {
    if (!document.getElementsByTagName('footer').length || !this.emma.current) return
    let footer =
      document.body.clientHeight -
      document.getElementsByTagName('footer')[0].clientHeight -
      window.innerHeight +
      this.state.distance;

    if (window.scrollY > footer) {
      let bottom = window.scrollY - footer + this.emma.current.clientHeight / 4

      this.setState({
        fixBottom: bottom + 70 > window.innerHeight ? window.innerHeight - 120 : bottom,
      });
    } else {
      this.setState({
        fixBottom: 24,
      });
    }

    if (window.scrollY > 400) this.openEmma();
    else this.closeEmma();
  };

  componentDidMount() {
    if (this.props.show) {
      window.addEventListener('scroll', e => {
        this.setPosition();
      });
    }

    let timer = null

    timer = setTimeout(() => {
      this.setPosition();
      clearInterval(timer);
    }, 5000)
  }

  openEmma() {
    if (!this.emma.current) return;
    this.emma.current.classList.add('is-open');
  }

  closeEmma() {
    if (!this.emma.current) return;
    this.emma.current.classList.remove('is-open');
    this.clearTimeout = setTimeout(() => {
      this.openEmma();
      clearTimeout(this.clearTimeout);
    }, 12000);
  }

  render() {
    return this.props.show ? (!this.state.isEbu && !this.state.isHelpCenter ? (
      <div
        ref={this.emma}
        className={`emma-service ${this.props.inline ? 'is-inline' : ''}`}
        style={{ bottom: this.state.fixBottom }}>
        <div className='avatar'></div>
        <div className='text'>免費諮詢</div>
      </div>
    ) : (
        <div
          ref={this.emma}
          className={`emma-service is-ebu ${this.props.inline ? 'is-inline' : ''}`}
          style={{ bottom: this.state.fixBottom }}>
          <div className='icon'>
            <img src={'/resources/common/images/chat.png'} height='24' alt='聯繫我們' />
          </div>
          <div className='text'>聯繫我們</div>
        </div>
      )) : null;
  }
}

EmmaService.propTypes = {
  show: PropTypes.bool, // Boolean
};

export default withRouter(EmmaService);

```
{% endtab %}
{% endtabs %}

Props

| Name | Type | Description |
| :--- | :--- | :--- |
| show | Boolean | 是否要顯示，預設為 false |

