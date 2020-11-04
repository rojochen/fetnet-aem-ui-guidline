---
description: 載入更多模組
---

# LoadMore

### LoadMore

{% tabs %}
{% tab title="狀態1（有更多資料）" %}
![](../.gitbook/assets/image%20%2879%29.png)
{% endtab %}

{% tab title="狀態2（無資料）" %}
![](../.gitbook/assets/image%20%2882%29.png)
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Usage" %}
```javascript
import LoadMore from '../components/LoadMore';

this.state = {
  currentArticleLoadMore: true,
};

loadMore = () => {
  // console.log(Mock.loadMoreData);
  this.setState({
    article: [...this.state.article, ...Mock.loadMoreData],
    currentArticleLoadMore: false,
  });
};

<LoadMore
  click={loadMore}
  load={currentArticleLoadMore}
  moreLabel='展開看更多'
  noMoreLabel='沒有更多文章'
/>
```
{% endtab %}

{% tab title="Source" %}
```javascript
import React, { Component } from 'react';
import { Link } from 'react-router-dom';
import PropTypes from 'prop-types';

export class LoadMore extends Component {
  render() {
    return (
      <div className='load-more'>
        {this.props.load ? (
          <Link to="#" onClick={this.props.click} className='expand'>
            {this.props.moreLabel}
            <i className={`icon-plus`}></i>
          </Link>
        ) : (
            this.props.noMoreLabel ? <p className='expand no-more'>
              <i className={`icon-no-more`} />
              {this.props.noMoreLabel}
            </p> : null

          )}
      </div>
    );
  }
}

LoadMore.propTypes = {
  moreLabel: PropTypes.string,
  noMoreLabel: PropTypes.string,
  load: PropTypes.bool,
  click: PropTypes.func,
};
export default LoadMore;

```
{% endtab %}
{% endtabs %}



#### Props

| Name | Type | Require | Description |
| :--- | :--- | :--- | :--- |
| moreLabel | string |  | 可以載入更多十顯示的文案 |
| noMoreLabel | string |  | 沒有更多時的文案 |
| load | bool |  | 有無更多的狀態 |
| click | func |  | 按下載入更多事件 |

