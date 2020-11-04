# Formsy

本專案使用 Formsy 作為表單驗證工具，表單模組都與 Formsy 做連結以偵測值的改變。使用方式如下：

## 基本設定

### 表單元件

{% code title="MyInput.js" %}
```jsx
import { withFormsy } from 'formsy-react';
import React from 'react';

class MyInput extends React.Component {
  constructor(props) {
    super(props);
    this.changeValue = this.changeValue.bind(this);
  }

  changeValue(event) {
    this.props.setValue(event.currentTarget.value);
  }

  render() {
    // An error message is returned only if the component is invalid
    const errorMessage = this.props.getErrorMessage();

    return (
      <div>
        <input onChange={this.changeValue} type="text" value={this.props.getValue() || ''} />
        <span>{errorMessage}</span>
      </div>
    );
  }
}

export default withFormsy(MyInput);
```
{% endcode %}

### 表單設定

```jsx
import Formsy from 'formsy-react';
import React from 'react';
import MyInput from './MyInput';

export default class App extends React.Component {
  constructor(props) {
    super(props);
    this.disableButton = this.disableButton.bind(this);
    this.enableButton = this.enableButton.bind(this);
    this.state = { canSubmit: false };
  }

  disableButton() {
    this.setState({ canSubmit: false });
  }

  enableButton() {
    this.setState({ canSubmit: true });
  }

  submit(model) {
    fetch('http://example.com/', {
      method: 'post',
      body: JSON.stringify(model),
    });
  }

  render() {
    return (
      <Formsy onValidSubmit={this.submit} onValid={this.enableButton} onInvalid={this.disableButton}>
        <MyInput name="email" validations="isEmail" validationError="This is not a valid email" required />
        <button type="submit" disabled={!this.state.canSubmit}>
          Submit
        </button>
      </Formsy>
    );
  }
}
```

## 表單驗證

### 元件設定

```jsx
<MyInput
  name="email"
  validations={{
    isEmail: true,
    maxLength: 50,
  }}
  validationErrors={{
    isEmail: 'You have to type valid email',
    maxLength: 'You can not type in more than 50 characters',
  }}
/>
```

### 錯誤訊息與必填樣式

```jsx
class MyInput extends React.Component {
  changeValue = event => {
    this.props.setValue(event.currentTarget.value);
  };
  render() {
    var className = this.props.showRequired ? 'required' : '';
    return (
      <div className={className}>
        <input type="text" onChange={this.changeValue} value={this.props.value} />
        <span>{this.props.errorMessage}</span>
      </div>
    );
  }
}
```

### 客製化驗證

```jsx
import { addValidationRule } from 'formsy-react';


// 增加規則 1 
addValidationRule('isFruit', function(values, value) {
  return ['apple', 'orange', 'pear'].indexOf(value) >= 0;
});

<MyInput name="fruit" validations="isFruit" />


// 增加規則 2 + 客製化錯誤訊息
<MyInput 
validations={{
    minLength: 10,
    isMobile: function (values, value) {
        return !value === false && value.length === 10 && /^09\d{8}$/.test(value)
            ? true
            : '請輸入正確的行動電話';
    },
}}
validationErrors={{
    isDefaultRequiredValue: '請輸入行動電話',
}}
/>
```

更多細節內容請參考 [formsy-react](https://github.com/formsy/formsy-react)。

## Form Submit

```jsx

class Form extends React.Component {
  constructor(props) {
    super(props);
    this.form = React.createRef();
    this.state = {
      // 判斷是否可送出表單
      canSubmit: true,    
      // 紀錄表單 value 與 required
      form: {
        step: { value: '0', required: true },
        business_type: { value: '0', required: true },
        your_need: { value: '0', required: true },
        comment: { value: '', required: false },
        name: { value: '', required: true },
        gender: { value: '', required: true },
        email: { value: '', required: true },
        mobile: { value: '', required: true },
        contact_time: { value: '', required: true },
        resources: { value: '0', required: false },
        agree: { value: '', required: true },
      },
    };
  }
  
  // 紀錄表單 value 的改變
  onChange = (name, value) => {
    let form = Object.assign(this.state.form);
    form[name] = value;
    this.setState({
      form: form,
    });
  }
  
  disableButton(model, resetForm, invalidateForm) {
    // 畫面移到有 error 的欄位
    setTimeout(() => {
      if(window.isIE) {
        let elem = window || document.documentElement
        elem.scroll(0, document.getElementsByClassName('is-invalid')[0].offsetTop);
      } else
        window.scrollTo(0, document.getElementsByClassName('is-invalid')[0].offsetTop);
    }, 100);
    
    this.setState({ canSubmit: false });
  }

  enableButton(model, resetForm, invalidateForm) {
    // debugger
    this.setState({ canSubmit: true });
  }

  submit(model) {
    // 表單送出
    console.log('submitted');
  }

  render() {
    return (
      <main className='fui-form'>
        
        <Formsy
          className='fui-container'
          onValidSubmit={this.submit}
          onValid={this.enableButton}
          onInvalidSubmit={this.disableButton}
          noValidate
          ref={this.form}>
          
          <div className='form-group'>
            <h4 className='form-description is-text-darkgray50'>花一分鍾填寫您的需求，即可獲得內行人的創業秘笈！</h4>
            <div className='is-text-accent text-sm'>
              <span className='required-dot'></span>為必填項目
            </div>
          </div>
          
          <RadioGroup
            validationErrors='請選擇階段'
            onChange={this.onChange}
            label='您目前的階段？'
            name='step'
            required={this.state.form.step.required}
            default={this.state.form.step.value}
            options={[
              {
                value: '0',
                label: '創業籌備',
                icon: {
                  default: '/resources/product/images/opt-1.png',
                  selected: '/resources/product/images/opt-1-selected.png',
                },
              },
              {
                value: '1',
                label: '成長擴展',
                icon: {
                  default: '/resources/product/images/opt-2.png',
                  selected: '/resources/product/images/opt-2-selected.png',
                },
              },
              {
                value: '2',
                label: '轉型升級',
                icon: {
                  default: '/resources/product/images/opt-3.png',
                  selected: '/resources/product/images/opt-3-selected.png',
                },
              },
            ]}
          />
          <CheckGroup
            onChange={this.onChange}
            validationErrors={{ isDefaultRequiredValue: '請選擇創業類型' }}
            label='創業類型？'
            name='business_type'
            required={this.state.form.business_type.required}
            default={this.state.form.business_type.value}
            options={[
              { value: '0', label: '餐飲' },
              { value: '1', label: '零售' },
              { value: '2', label: '其他' },
            ]}
          />
          
          <CheckGroup
            onChange={this.onChange}
            validationErrors={{ isDefaultRequiredValue: '請選擇您的需求' }}
            label='您的需求？'
            name='your_need'
            required={this.state.form.your_need.required}
            default={this.state.form.your_need.value}
            options={[
              { value: '0', label: '找創業資金' },
              { value: '1', label: '選地點開店' },
              { value: '2', label: '穩定通訊上網' },
              { value: '3', label: '經營熟客關係' },
              { value: '4', label: '提升商品銷售' },
            ]}
          />
          <LabelTextarea
            name='comment'
            required={this.state.form.comment.required}
            value={this.state.form.comment.value}
            label='還有其他需求想讓我們知道嗎？'
            placeholder='您可以在此輸入需求...'
            maxLength={200}
            onChange={this.onChange}
          />

          <Grid container spacing={2} className='input-row'>
            <Grid item xs={12} sm={12} md={6}>
              <LabelInput
                validationErrors={{
                  isDefaultRequiredValue: '請輸入您的姓名',
                }}
                name='name'
                required={this.state.form.name.required}
                value={this.state.form.name.value}
                label='姓名'
                onChange={this.onChange}
              />
            </Grid>
            <Grid item xs={12} sm={12} md={6}>
              <div className='radio-to-bottom radio-sex'>
                <RadioButtons
                  name='gender'
                  options={[
                    { value: '0', label: '先生' },
                    { value: '1', label: '女士' },
                  ]}
                  selected='0'
                  getSelected={e => this.onChange('gender', e)}
                />
              </div>
            </Grid>
            <Grid item xs={12} sm={12} md={6}>
              <LabelInput
                validations='isEmail'
                validationErrors={{
                  isEmail: '請輸入正確的 Email',
                  isDefaultRequiredValue: '請輸入 Email',
                }}
                name='email'
                required={this.state.form.email.required}
                value={this.state.form.email.value}
                label='Email'
                onChange={this.onChange}
              />
            </Grid>
            <Grid item xs={12} sm={12} md={6}>
              <LabelInput
                validations={{
                  minLength: 10,
                  isMobile: function(values, value) {
                    return !value === false && value.length === 10 && /^09\d{8}$/.test(value)
                      ? true
                      : '請輸入正確的行動電話';
                  },
                }}
                validationErrors={{
                  isDefaultRequiredValue: '請輸入行動電話',
                }}
                name='mobile'
                required={this.state.form.mobile.required}
                value={this.state.form.mobile.value}
                label='行動電話'
                onChange={this.onChange}
              />
            </Grid>
            <Grid item md={12}>
              <RadioButtons
                label='方便聯繫您的時間'
                required
                validationErrors={{ isDefaultRequiredValue: '請選擇方便聯繫您的時間' }}
                name='contact_time'
                options={[
                  { value: '3', label: '17:00-19:00' },
                  { value: '1', label: '10:00-12:00' },
                  { value: '2', label: '14:00-17:00' },
                  { value: '0', label: '不指定時間' },
                ]}
                selected='3'
                getSelected={e => this.onChange('contact_time', e)}
              />
            </Grid>
          </Grid>

          <CheckboxButtons
            label='您在哪些地方看過此資訊？(可複選)'
            name='resources'
            options={[
              { value: '1', label: '公開課程' },
              { value: '2', label: 'FB廣告' },
              { value: '3', label: '網路廣告' },
              { value: '4', label: '網路搜尋' },
              { value: '5', label: '雜誌廣告' },
              { value: '6', label: '親友推薦' },
              { value: '7', label: '計程車廣告' },
              { value: '8', label: '其他' },
            ]}
            onChange={this.onChange}
          />
          <div className='input-group'>
            <div className='recaptcha'>
              <img src='https://cldup.com/p-jwfiXPY0-3000x3000.png' alt='recaptcha' />
            </div>
            <CheckboxCollapse
              name='agree'
              required
              validationErrors={{ isDefaultRequiredValue: '請同意個人資料保護法第8條所為之告知事情' }}
              collapseContent={`<p>公務機關或非公務機關依第十五條或第十九條規定向當事人蒐集個人資料時，應明確告知當事人下列事項：</p>
                        <p>
                        一、公務機關或非公務機關名稱。<br/>
                        二、蒐集之目的。<br/>
                        三、個人資料之類別。<br/>
                        四、個人資料利用之期間、地區、對象及方式。<br/>
                        五、當事人依第三條規定得行使之權利及方式。<br/>
                        六、當事人得自由選擇提供個人資料時，不提供將對其權益之影響。<br/>
                        有下列情形之一者，得免為前項之告知：
                        一、依法律規定得免告知。<br/>
                        二、個人資料之蒐集係公務機關執行法定職務或非公務機關履行法定義務
                            所必要。<br/>
                        三、告知將妨害公務機關執行法定職務。<br/>
                        四、告知將妨害公共利益。<br/>
                        五、當事人明知應告知之內容。<br/>
                        六、個人資料之蒐集非基於營利之目的，且對當事人顯無不利之影響。</p>`}
              label='我已知悉並了解遠傳依個人資料保護法第8條所為之告知事情'
              getCheckbox={e => this.onChange('agree', e)}
              checked={false}
            />
          </div>

          <button className={`is-large fui-button is-primary m-0`} disabled={!this.state.canSubmit}>
            <span className='text'>確認送出</span>
          </button>
        </Formsy>
      </main>
    );
  }
}


export default Form;
```

