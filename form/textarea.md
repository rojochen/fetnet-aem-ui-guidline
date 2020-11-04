# Textarea

{% tabs %}
{% tab title="Usage" %}
```jsx
import Formsy from 'formsy-react';
import LabelTextarea from '../components/form/LabelTextarea';


class Login extends React.Component {
  constructor(props) {
    super(props);
    this.form = React.createRef();
    this.state = {
      canSubmit: true,
      form: {
        comment: { value: '', required: false },
      },
    };

  }

  disableButton() {
    this.setState({ canSubmit: false });
  }

  enableButton() {
    this.setState({ canSubmit: true });
  }
  
  render() {
    return (
      <Formsy onValid={this.enableButton} onInvalid={this.disableButton}>
          <LabelTextarea
            name='comment'
            required={this.state.form.comment.required}
            value={this.state.form.comment.value}
            label='還有其他需求想讓我們知道嗎？'
            placeholder='您可以在此輸入需求...'
            maxLength={200}
            onChange={this.onChange}
          />
      </Formsy>
    )
  }
}
```
{% endtab %}

{% tab title="LabelTextarea.js" %}
    import React from 'react';
    import { withFormsy } from 'formsy-react';
    import PropTypes from 'prop-types';

    class LabelTextarea extends React.Component {
        constructor(props) {
            super(props);
            this.input = React.createRef();
            this.state = {
                isFocus: false,
                required: this.props.required || false,
                placeholder: this.props.placeholder || '您可以在此輸入需求...',
                maxLength: this.props.maxLength || 450
            }

            this.handleChange = this.handleChange.bind(this)
        }

        componentDidMount() {
            this.input.current.value = this.props.getValue();
        }

        setFocus = event => {
            this.setState({
                isFocus: true
            })
        }

        setBlur = event => {
            this.setState({
                isFocus: false
            })
        }

        handleChange = (event) => {
            let val = event.currentTarget.value
            if (val.length > this.state.maxLength) return false;
            this.setState({value: val})
            this.props.onChange(this.props.name, val)
        }

        render() {
            return (
                <div className={`form-group`}>
                    <label htmlFor={`textarea-${this.props.name}`} className={this.state.required ? 'is-required' : ''}>{this.props.label}</label>
                    <div className={`fui-textarea ${this.state.isFocus ? 'is-focus' : ''}`}>
                        <textarea 
                        id={`textarea-${this.props.name}`}
                        name={this.props.name} 
                        ref={this.input} 
                        placeholder={this.props.placeholder} 
                        value={this.props.getValue() || ''}
                        onBlur={this.setBlur}
                        onFocus={this.setFocus}
                        onKeyPress={this.handleChange} 
                        onChange={this.handleChange}></textarea>
                        <div className="max-length-counter">
                            {(this.props.getValue()).length} / {this.state.maxLength}
                        </div>
                    </div>
                </div>
            )
        }
    }

    LabelTextarea.propTypes = {
        required: PropTypes.bool,
        label: PropTypes.string.isRequired,
        name: PropTypes.string.isRequired,
        placeholder: PropTypes.string,
        value: PropTypes.string,
        maxLength: PropTypes.number,
        onChange: PropTypes.func
    }

    export default withFormsy(LabelTextarea);
{% endtab %}
{% endtabs %}

#### Properties

| 名稱 | 屬性 | 必填 | 選項 | 說明 |
| :--- | :--- | :--- | :--- | :--- |
| name | String | true |  | 輸入框名稱 |
| placeholder | String |  |  | 輸入框提示訊息 |
| validations | String or Object |  |  | 驗證條件 |
| validationError | String or Object |  |  | 錯誤訊息 |
| required | Boolean |  |  | 是否為必填 |
| label | String |  |  | 標題 |
| value | String |  |  | 值 |
| maxLength | Number |  |  | 可輸入最大字數 |
| onChange | Function |  |  | 輸入框值改變事件 |

