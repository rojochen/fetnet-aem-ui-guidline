# Dropdown

## Default

Dropdown 廣泛運用於表單及各式下拉選單，在不同模組下，會帶入不同樣式；資料除了必填項目外，其餘項目依模組需要自行選填。

{% tabs %}
{% tab title="Dropdown.js" %}
```jsx
import React from 'react';
import Menu from './Menu';
import Item from './item/LinkItem';
import PropTypes from 'prop-types';

class Dropdown extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      anchorEl: null,
      isClose: false,
      selectedItem: this.props.label,
      isHandleClick: false,
    };

    this.getSelected = this.getSelected.bind(this);
  }

  componentDidMount() {
    this.setState({
      selectedItem: this.props.label,
    });
  }

  componentDidUpdate(prevProps) {
    if (
      prevProps.label !== this.state.selectedItem ||
      (
        prevProps.list.length !== this.props.list.length ||
        (
          prevProps.list.length &&
          prevProps.list[0].text !== this.props.list[0].text &&
          prevProps.list[0].value !== this.props.list[0].value
        )
      )
    ) {
      this.setState({
        selectedItem: this.props.label,
      });
    }
  }

  closeMenu = event => {
    if (this.props.close) this.props.close();
    setTimeout(() => {
      this.setState({
        anchorEl: null,
        isClose: false,
      });
    }, 120);
  };

  handleClick = e => {
    e.preventDefault();

    if (this.state.isClose === true) return;
    this.setState({ isHandleClick: true });
    this.forceUpdate();

    if (Boolean(this.state.anchorEl)) {
      this.setState({
        anchorEl: null,
        isHandleClick: false,
      });
    } else {
      this.setState({
        anchorEl: e.currentTarget,
        isHandleClick: false,
      });
    }
  };

  selectItem = (item, idx) => {
    if (window.event.preventDefault) window.event.preventDefault();
    else window.event.returnValue = false;

    this.setState({
      selectedItem: item.text,
    });

    if (this.props.onChange) this.props.onChange(item, idx);
    this.closeMenu();
  };

  getSelected = item => {
    return this.state.selectedItem === item.text ? 'active' : '';
  };
  readyToClose = item => {
    if (this.state.isHandleClick === true) return;
    this.setState({
      isClose: true,
    });
    this.forceUpdate();

    setTimeout(() => {
      this.closeMenu();
    }, 50);
  };

  render() {
    return (
      <div
        className={`
                fui-dropdown 
                ${this.props.arrow ? 'with-arrow' : ''} 
                ${this.props.className ? this.props.className : ''}
                ${Boolean(this.state.anchorEl) ? 'is-show' : ''} 
                `}
        onClick={this.props.onActive}>
        <button
          aria-haspopup='true'
          aria-expanded={Boolean(this.state.anchorEl)}
          aria-label={this.props.label}
          onClick={this.handleClick}
          className='fui-dropdown-item'>
          <span dangerouslySetInnerHTML={{ __html: this.state.selectedItem }}></span>
          {this.props.arrow ? <i className='icon-chevron-down'></i> : ''}
        </button>
        <Menu
          anchorEl={this.state.anchorEl}
          keepMounted
          open={Boolean(this.state.anchorEl)}
          onClose={this.readyToClose}>
          <div className='menu-wrapper'>
            {this.props.list.map((item, idx) => (
              <Item
                className={`${
                  this.state.selectedItem === item.text || this.props.value === item.value ? 'active' : ''
                  } ${this.props.hasCheck ? 'check-icon' : ''}`}
                key={'menu-item' + this.props.id + idx}
                onClick={e => this.selectItem(item, idx)}>
                {item.text}
              </Item>
            ))}
          </div>
        </Menu>
      </div>
    );
  }
}

Dropdown.defaultProps = {
  hasCheck: false,
  onActive: null,
};
Dropdown.propTypes = {
  list: PropTypes.arrayOf(Item),
  arrow: PropTypes.bool, // Boolean
  className: PropTypes.string,
  label: PropTypes.string.isRequired,
  value: PropTypes.string,
  onChange: PropTypes.func, // callback
  onActive: PropTypes.func,
  hasCheck: PropTypes.bool,
};

export default Dropdown;

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
      <td style="text-align:left">list</td>
      <td style="text-align:left">Array</td>
      <td style="text-align:left">&lt;code&gt;&lt;/code&gt;</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>&#x4F7F;&#x7528; <a href="https://app.gitbook.com/@ajacreative/s/fetnet-1/~/drafts/-M1PX30KNQdcrffdEZXC/elements/item">Item</a> &#x7684;&#x8CC7;&#x6599;&#x7D50;&#x69CB;&#xFF0C;&#x4E3B;&#x8981;&#x4F7F;&#x7528;&#x6B04;&#x4F4D;&#x5982;&#x4E0B;&#xFF1A;</p>
        <p><code>{<br /> text: String,<br /> item: String,<br />}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">label</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">true</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x4E0B;&#x62C9;&#x9078;&#x55AE;&#x9810;&#x8A2D;&#x6587;&#x5B57;&#xFF0C;&#x8207;&#x88AB;&#x9078;&#x64C7;&#x5F8C;&#x8981;&#x5448;&#x73FE;&#x7684;&#x5167;&#x5BB9;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">value</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x88AB;&#x9078;&#x64C7;&#x7684;&#x503C;&#xFF0C;&#x9810;&#x8A2D;&#x70BA;&#x7A7A;&#x503C;</td>
    </tr>
    <tr>
      <td style="text-align:left">className</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x53EF;&#x5E36;&#x5165;&#x6A23;&#x5F0F;&#xFF0C;&#x4E3B;&#x8981;&#x7528;&#x65BC;&#x5728;&#x500B;&#x5225;&#x6A21;&#x7D44;&#x4E2D;&#x7684;&#x7368;&#x7ACB;&#x8A2D;&#x5B9A;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">arrow</td>
      <td style="text-align:left">Boolean</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x662F;&#x5426;&#x8981;&#x51FA;&#x73FE;&#x7BAD;&#x982D;</td>
    </tr>
    <tr>
      <td style="text-align:left">onChange</td>
      <td style="text-align:left">Function</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>&#x56DE;&#x50B3;&#x88AB;&#x9078;&#x53D6;&#x7684;&#x9805;&#x76EE;&#x8207;&#x7D22;&#x5F15;&#x503C;&#x3002;</p>
        <p><code>onChange( { text, value }, index ) {</code>
        </p>
        <p><code>   ...<br />}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">onActive</td>
      <td style="text-align:left">Function</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">Dropdown &#x88AB;&#x89F8;&#x767C;&#x4E8B;&#x4EF6;&#xFF0C;&#x7528;&#x65BC;
        <a
        href="https://app.gitbook.com/@ajacreative/s/fetnet-1/~/drafts/-M1PX30KNQdcrffdEZXC/components/panel#has-more-tab">HasMoreTab</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">hasCheck</td>
      <td style="text-align:left">Boolean</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">&#x88AB;&#x9078;&#x53D6;&#x7684;&#x9805;&#x76EE;&#x662F;&#x5426;&#x51FA;&#x73FE;&#x52FE;&#x52FE;&#x6A19;&#x8A18;&#xFF0C;&#x7528;&#x65BC;&#x9996;&#x9801;&#x6A23;&#x5F0F;&#x3002;</td>
    </tr>
  </tbody>
</table>

## DropdownTab

處理網頁中在大網為 Tab，小網為 Dropdown 的樣式。

{% code title="DropdownTab.js" %}
```jsx
import React from 'react';
import Tab from './Tab';
import PropTypes from 'prop-types';

class DropdownTab extends React.Component {
    constructor(props) {
        super(props);
        this.menu = React.createRef();
        this.state = {
            menuHeight: 0,
            currentTab: this.props.default || 0,
            menuOpen: false
        };
        
        this.setMenuHeight = this.setMenuHeight.bind(this)
    }

    componentDidMount() {
        this.setMenuHeight()

        window.addEventListener('resize', e => {
            this.setMenuHeight()
        })
    }
    
    setMenuHeight() {
        if(!this.menu.current) return;
        
        this.setState({
            menuHeight: this.menu.current.children[0].clientHeight
        })
    }

    toggleMenu() {
        this.setState({
            menuOpen: !this.state.menuOpen
        })
    }
    
    closeMenu() {
        this.setState({
            menuOpen: false
        })
    }

    onChange(e) {
        this.closeMenu()
        this.setState({
            currentTab: e
        })
        this.props.onChange(e)
    }
    
    handleChange(index) {
        this.closeMenu()
        this.setState({
            currentTab: index
        })
    }

    render() {
        return (
            <div className="fui-tab-container mobile-dropdown">
                <button className="display" onClick={e => this.toggleMenu(e)}>
                    <span>{this.props.tabs.list[this.state.currentTab].label}</span>
                    <i className="icon-chevron-down"></i>
                </button>
                <div 
                className="fui-menu" 
                ref={this.menu} 
                style={{height: this.state.menuOpen ? this.state.menuHeight : 0 }}>
                    <Tab 
                    {...this.props.tabs} 
                    default={this.props.default}
                    className={`${this.state.menuOpen ? 'is-open' : ''}`} 
                    onChange={e => this.onChange(e)} />
                </div>
            </div>
        )
    }
}


DropdownTab.propTypes = {
    default: PropTypes.number,
    tabs: PropTypes.shape({
        name: PropTypes.string,
        list: PropTypes.arrayOf(
            PropTypes.shape({
                icon: PropTypes.string,
                focusIcon: PropTypes.string,
                label: PropTypes.string.isRequired,
                link: PropTypes.string
            })
        )
    }),
    onChange: PropTypes.func
}

export default DropdownTab;
```
{% endcode %}

#### Properties

| 名稱 | 屬性 | 選項 | 必填 | 說明 |
| :--- | :--- | :--- | :--- | :--- |
| default | Number | \`\` |  | 預設選取的索引值 |
| tabs | Object |  |  | 使用 [Tab](https://app.gitbook.com/@ajacreative/s/fetnet-1/~/drafts/-M1PX30KNQdcrffdEZXC/components/tab)  的資料結構，取用 name 和 list 項目 |
| onChange | Function |  |  |  |

## Related Component

* [Select](https://app.gitbook.com/@ajacreative/s/fetnet-1/~/drafts/-M1PX30KNQdcrffdEZXC/form/select)
* [HasMoreTab](https://app.gitbook.com/@ajacreative/s/fetnet-1/~/drafts/-M1PX30KNQdcrffdEZXC/components/panel#has-more-tab)
* NavContentTab1
* DropdownMenu

