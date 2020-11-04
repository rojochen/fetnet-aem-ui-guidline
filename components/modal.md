---
description: 彈窗
---

# Modal

### VideoModal

{% tabs %}
{% tab title="Desktop" %}
![](../.gitbook/assets/image%20%28170%29.png)
{% endtab %}

{% tab title="Mobile" %}
![](../.gitbook/assets/image%20%2897%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Usage" %}
```javascript
import VideoModal from '../components/VideoModal';

<VideoModal 
    open={this.state.modalOpen} 
    videoUrl={this.state.currentVideo} 
    alterVideo={this.state.alterVideo} 
    onClose={this.closeModal} 
/>
```
{% endtab %}

{% tab title="Source" %}
```javascript
import React from 'react';
import YouTube from 'react-youtube';
import ReactPlayer from 'react-player'

class VideoModal extends React.Component {
  constructor(props) {
    super(props);
    this.modal = React.createRef();
    this.state = {
      open: false,
      videoUrl: '',
      alterVideo: ''
    };
  }

  componentDidUpdate() {
    if (this.props.open !== this.state.open) {
      let $htmlTag = document.getElementsByTagName('html')[0];
      this.setState({
        open: this.props.open,
      });

      if (this.props.open) {
        $htmlTag.classList.add('modal-open');
        this.modal.current.classList.add('is-open');
      } else {
        this.modal.current.classList.add('is-closing');
        setTimeout(() => {
          this.modal.current.className = 'fui-modal';
          $htmlTag.classList.remove('modal-open');
        }, 500);
      }
    }

    if (this.props.videoUrl !== this.state.videoUrl || this.props.alterVideo !== this.state.alterVideo) {
      this.setState({
        videoUrl: this.props.videoUrl,
        alterVideo: this.props.alterVideo
      });
      this.forceUpdate();
    }
  }

  getVideoId(url) {
    if (url.indexOf('v=') > -1) {
      return url.split('v=')[1];
    } else {
      return url.split(/\//g).reverse()[0];
    }
  }

  closeModal = e => {
    e.preventDefault();
    this.props.onClose();
  };

  onReady(event) {
    event.target.playVideo();
  }

  render() {
    const opt = {
      playerVars: {
        enablejsapi: 1,
      },
    };

    return (
      <div ref={this.modal} className={`fui-modal`}>
        <div className='fui-modal-header'>
          <button className='fui-close' onClick={this.closeModal}>
            <i className='icon-close'></i>
          </button>
        </div>
        <div className='fui-modal-content'>
          <div className='fui-modal-body'>
            {this.state.videoUrl ? (
              <YouTube
                videoId={this.getVideoId(this.state.videoUrl)}
                opt={opt}
                onReady={this.onReady}
                containerClassName='fui-player'
              />
            ) : (
                <ReactPlayer url={this.state.alterVideo} playing={true} controls={true} />
              )}

          </div>
        </div>
      </div>
    );
  }
}

export default VideoModal;

```
{% endtab %}
{% endtabs %}

#### Props

| Name | Type | Require | Description |
| :--- | :--- | :--- | :--- |
| open | bool | true | 觸發開啟事件 |
| videoUrl | string |  | youtube連結 |
| alterVideo | string |  | 替代youtube連結，目前支援mp4，二擇一 |
| onClose | func | true | 觸發關閉事件 |

### ImageModal

{% tabs %}
{% tab title="Desktop" %}
![](../.gitbook/assets/image%20%28202%29.png)
{% endtab %}

{% tab title="MObile" %}
![](../.gitbook/assets/image%20%2812%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Usage" %}
```javascript
import ImageModal from '../components/ImageModal'

<ImageModal 
    mainSrc={'//placekitten.com/1500/1000'} 
    onCloseRequest={() => doSomething()} 
/>
```
{% endtab %}

{% tab title="Source" %}
```javascript
import ImageModal from './react-image-lightbox';
import PropTypes from 'prop-types';

ImageModal.propTypes = {
  mainSrc: PropTypes.string,
  onCloseRequest: PropTypes.func
}

export default ImageModal;

```
{% endtab %}
{% endtabs %}

#### Props

| Name | Type | Require | Description |
| :--- | :--- | :--- | :--- |
| mainSrc | string | true | 圖片連結 |
| onCloseRequest | func |  | 關閉事件 |

### ErrorModal

![](../.gitbook/assets/image%20%28108%29.png)

{% tabs %}
{% tab title="Usage" %}
```javascript
import ErrorModal from '../components/ErrorModal';

<ErrorModal 
    open={this.state.modalOpen} 
    errorContent={this.state.errorContent} 
    onClose={this.closeModal} 
/>
```
{% endtab %}

{% tab title="Source" %}
```javascript
import React from 'react';
import Button from '../components/Button';
import PropTypes from 'prop-types';

class ErrorModal extends React.Component {
  constructor(props) {
    super(props);
    this.modal = React.createRef();
    this.state = {
      open: false,
      errorContent: '',
    };
  }

  componentDidUpdate() {
    if (this.props.open !== this.state.open) {
      let $htmlTag = document.getElementsByTagName('html')[0];
      this.setState({
        open: this.props.open,
      });

      if (this.props.open) {
        $htmlTag.classList.add('modal-open');
        this.modal.current.classList.add('is-open');
      } else {
        this.modal.current.classList.add('is-closing');
        setTimeout(() => {
          this.modal.current.className = 'fui-modal';
          $htmlTag.classList.remove('modal-open');
        }, 500);
      }
    }
  }

  closeModal = () => {
    this.props.onClose();
  };

  render() {
    return (
      <div ref={this.modal} className={`fui-modal`}>
        <div className='fui-modal-content'>
          <div className='fui-modal-body'>
            <div className='error-modal'>
              <div className='subtitle is-text-medium mb-2'>
                系統因忙碌暫時發生問題，
                <br />
                請重新操作或稍後再試。
              </div>
              <div className='body1 mb-3'>{this.props.errorContent}</div>
              <Button onClick={this.closeModal} btnStyle='primary' className='fui-button is-primary m-0'>
                確認
              </Button>
            </div>
          </div>
        </div>
      </div>
    );
  }
}

ErrorModal.propTypes = {
  open: PropTypes.bool,
  errorContent: PropTypes.string,
  onClose: PropTypes.func,
};
export default ErrorModal;

```
{% endtab %}
{% endtabs %}



#### Props

| Name | Type | Require | Description |
| :--- | :--- | :--- | :--- |
| open | bool |  | true=打開，false=關閉 |
| errorContent | string |  | 錯誤訊息內容 |
| onClose | func |  | 關閉事件 |

