# Select

{% tabs %}
{% tab title="Usage" %}
```jsx
import Select from '../../components/form/Select';
import Formsy from 'formsy-react';

class Consultation extends React.Component {
  render () {
    return (
      <Formsy
        onValid={this.enableButton}
        onInvalidSubmit={this.disableButton}
        ref={this.form}>
        
          <Select
            validationErrors={{
              isDefaultRequiredValue: '請選擇產品/服務級別',
            }}
            name='product_service_1'
            required={this.state.form.product_service_1.required}
            options={[
              { text: '行動服務', value: 1 },
              { text: '固網服務', value: 2 },
              { text: '雲端服務', value: 3 },
              { text: '物聯網', value: 4 },
              { text: '資安服務', value: 5 },
            ]}
            value={this.state.form.product_service_1.value}
            label='請選擇產品/服務級別'
            onChange={this.onChange}
          />
          
      </Formsy>
    )
  }
}
```
{% endtab %}

{% tab title="Select.js" %}
```jsx
import React from 'react';
import { withFormsy } from 'formsy-react';
import Dropdown from '../Dropdown';
import PropTypes from 'prop-types';

class Select extends React.Component {
  constructor(props) {
    super(props);
    this.selector = React.createRef();
    this.state = {
      submitted: false,
      isInvalid: false,
      label: this.props.label || this.getSelectedItem()
    };
  }

  componentDidMount() {
    this.selector.current.value = this.props.getValue();
  }

  componentDidUpdate(prevProps) {
    if (
      this.props.isFormSubmitted() !== this.state.submitted
      ||
      (this.props.getValue() && this.getSelectedItem(this.props.getValue()) !== this.state.label)
    ) {
      console.log('componentDidUpdate', this.getSelectedItem(this.props.getValue()))
      this.setState({
        label: this.getSelectedItem(this.props.getValue()),
        submitted: this.props.isFormSubmitted(),
        isInvalid: this.props.showRequired() || this.props.showError(),
      });
    }
  }

  doClose = () => {
    this.setState({
      isInvalid: this.props.showRequired() || this.props.showError(),
    });
  };

  changeValue = select => {
    this.selector.current.value = select.value;
    this.props.setValue(select.value)

    this.setState({
      label: (this.getSelectedItem(select.value)),
      isInvalid: this.props.showRequired() || this.props.showError(),
    });

    this.forceUpdate()

    if (this.props.onChange) this.props.onChange(this.props.name, select.value);

  };

  getSelectedItem(value) {
    if (value === '') {
      return '';
    } else {
      let opt = this.props.options.filter(opt => opt.value === value)
      return opt.length ? opt[0].text : ''
    }
  }

  render() {
    const errorMessage = this.props.getErrorMessage();

    return (
      <div className='fui-select'>
        <select name={this.props.name} ref={this.selector} disabled={this.props.disabled} defaultValue={this.props.getValue() || ''}>
          {this.props.options.map((opt, i) => (
            <option key={`fui-select-${i}`} value={opt.value}>
              {opt.text}
            </option>
          ))}
        </select>
        <Dropdown
          id={this.props.name}
          className="is-button"
          label={this.state.label}
          list={this.props.options}
          onChange={this.changeValue}
          arrow={true}
          close={this.doClose}
        />
        {this.state.isInvalid ? <span className='error-message'>{errorMessage}</span> : ''}
      </div>
    );
  }
}

Select.propTypes = {
  label: PropTypes.string,
  name: PropTypes.string,
  disabled: PropTypes.bool,
  options: PropTypes.arrayOf(
    PropTypes.shape({
      text: PropTypes.string,
      value: PropTypes.string,
    })
  ),
  value: PropTypes.string,
  onChange: PropTypes.func,
};

export default withFormsy(Select);

```
{% endtab %}
{% endtabs %}

#### Properties

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x540D;&#x7A31;</th>
      <th style="text-align:left">&#x5C6C;&#x6027;</th>
      <th style="text-align:left">&#x5FC5;&#x586B;</th>
      <th style="text-align:left">&#x9078;&#x9805;</th>
      <th style="text-align:left">&#x8AAA;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">true</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x8F38;&#x5165;&#x6846;&#x540D;&#x7A31;</td>
    </tr>
    <tr>
      <td style="text-align:left">validations</td>
      <td style="text-align:left">String or Object</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x9A57;&#x8B49;&#x689D;&#x4EF6;</td>
    </tr>
    <tr>
      <td style="text-align:left">validationError</td>
      <td style="text-align:left">String or Object</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x932F;&#x8AA4;&#x8A0A;&#x606F;</td>
    </tr>
    <tr>
      <td style="text-align:left">required</td>
      <td style="text-align:left">Boolean</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x662F;&#x5426;&#x70BA;&#x5FC5;&#x586B;</td>
    </tr>
    <tr>
      <td style="text-align:left">label</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x6A19;&#x984C;</td>
    </tr>
    <tr>
      <td style="text-align:left">options</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>{</p>
        <p>value: String,</p>
        <p>text: String</p>
        <p>}</p>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">value</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x9810;&#x8A2D;&#x503C;</td>
    </tr>
    <tr>
      <td style="text-align:left">disabled</td>
      <td style="text-align:left">Boolean</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x662F;&#x5426; disabled &#x72C0;&#x614B;</td>
    </tr>
    <tr>
      <td style="text-align:left">onChange</td>
      <td style="text-align:left">Function</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x8F38;&#x5165;&#x6846;&#x503C;&#x6539;&#x8B8A;&#x4E8B;&#x4EF6;</td>
    </tr>
  </tbody>
</table>

