# collapse

## CollapseMenu

```
import CollapseMenu from '../../components/partials/collapse/CollapseMenu';
<CollapseMenu
  menu={{
  name: '搜尋結果分類',
  content: [
      {
          id: '0',
          name: '所有結果 (0)',
          link: '',
      },
  ],
  }}
  selectMenu={this.changeMenu}
/>

```

#### Properties

| 名稱          | 屬性 | 選項 | 必填 | 說明 |
| :------------ | :--- | :--- | :--- | :--- |
| searchTagItem | obj  |      |      |      |
| selectMenu    | func |      |      |      |
| onClickTag    | func |      |      |      |
| showMore      | bool |      |      |      |
| menu          | obj  |      |      |      |

```
CollapseMenu.propTypes = {
  menu: PropTypes.shape({
    id: PropTypes.any,
    name: PropTypes.string.isRequired,
    content: PropTypes.arrayOf(
      PropTypes.shape({
        id: PropTypes.any,
        name: PropTypes.string.isRequired,
        link: PropTypes.string,
        content: PropTypes.arrayOf(
          PropTypes.shape({
            id: PropTypes.any,
            name: PropTypes.string,
            link: PropTypes.string,
          })
        ),
      })
    ),
  }),
  searchTagItem: PropTypes.object,
  selectMenu: PropTypes.func,
  onClickTag: PropTypes.func,
  showMore: PropTypes.bool
};
```

## CollapseMenuThirdLevel

```
import { CollapseMenu as Menu } from '../components/partials/collapse/CollapseMenuThirdLevel';
<Menu
  selectMenu={this.selectMenu}
  menu={{
    name: '常見問題分類',
    currentSelected: '',
    content: [
      // {
      //   name: '熱門優惠',
      //   id: 'a',
      // },
      {
        name: '4.5G語音+上網',
        id: 'b',
        content: [
          {
            name: '單門號',
            id: 'b01',
            content: [
              {
                name: '單單單門號',
                id: 'b011',
              },
              {
                name: '單單單門號2',
                id: 'b012',
              },
            ]
          },
          {
            name: '上網微微飽',
            id: 'b02',
            content: [
              {
                name: '上網微微微飽',
                id: 'b021',
              },
              {
                name: '上網微微微飽2',
                id: 'b022',
              },
            ]
          },
          {
            name: '飆網吃到飽',
            id: 'b03',
            content: [
              {
                name: '飆網吃到飽飽',
                id: 'b031',
              },
              {
                name: '飆網吃到飽飽飽',
                id: 'b032',
              },
            ]
          },
          {
            name: '上網搭手機',
            id: 'b04',
          },
          {
            name: '上網搭家電',
            id: 'b05',
          },
          {
            name: '上網搭寬頻',
            id: 'b06',
          },
          {
            name: '上網搭生活娛樂',
            id: 'b06',
          },
        ],
      },
      {
        name: '推薦續約',
        id: 'c',
        content: [
          {
            name: '行銷01',
            id: 'c01',
            link: '/123'
          },
          {
            name: '行銷02',
            id: 'c02',

            content: [
              {
                name: '行銷021',
                id: 'c031',
              },
              {
                name: '行銷022',
                id: 'c032',
              },
            ]
          },
        ],
      },
      {
        name: '網路門市限定',
        id: 'd'
      },
      {
        name: '家用上網',
        id: 'e'
      },
      {
        name: '遠傳易付卡',
        id: 'f'
      },
      {
        name: '出國上網',
        id: 'g'
      },
      {
        name: '用戶專屬優惠',
        id: 'h'
      },
      {
        name: 'friDay優惠',
        id: 'i'
      },
    ],
  }}
/>
```

#### Properties

| 名稱          | 屬性 | 選項 | 必填 | 說明 |
| :------------ | :--- | :--- | :--- | :--- |
| menu          | obj  |      |      |      |
| searchTagItem | obj  |      |      |      |
| selectMenu    | func |      |      |      |
| onClickTag    | func |      |      |      |
| showMore      | bool |      |      |      |

```
CollapseMenu.propTypes = {
  menu: PropTypes.shape({
    id: PropTypes.any,
    name: PropTypes.string.isRequired,
    content: PropTypes.arrayOf(
      PropTypes.shape({
        id: PropTypes.any,
        name: PropTypes.string.isRequired,
        link: PropTypes.string,
        content: PropTypes.arrayOf(
          PropTypes.shape({
            id: PropTypes.any,
            name: PropTypes.string,
            link: PropTypes.string,
          })
        ),
      })
    ),
  }),
  searchTagItem: PropTypes.object,
  selectMenu: PropTypes.func,
  onClickTag: PropTypes.func,
  showMore: PropTypes.bool
};
```

## CollapsePaper

```
import CollapsePaper from '../../components/collapse/CollapsePaper';
<CollapsePaper
  title="單價說明"
  className="collapse-table"
  openCollapse={e => { console.log(e) }}
  open={false}
>
...content
<CollapsePaper />
```

#### Properties

| 名稱         | 屬性   | 選項 | 必填 | 說明 |
| :----------- | :----- | :--- | :--- | :--- |
| title        | string |      | true |      |
| className    | string |      |      |      |
| children     | any    |      |      |      |
| openCollapse | func   |      |      |      |
| date         | string |      |      |      |

```
CollapsePaper.propTypes = {
    className: PropTypes.string,
    title: PropTypes.string.isRequired,
    open: PropTypes.bool,
    children: PropTypes.any,
    openCollapse: PropTypes.func,
    date: PropTypes.string,
}
```

## CollapsePaper2
```
import CollapsePaper2 from '../../components/partials/collapse/CollapsePaper2';
<CollapsePaper2 {...{
                                    collapseList: [
                                        {
                                            title: `<h6 class="h6-title">遠傳行動客服 APP 儲值</h6>`,
                                            content: `<h6 class="paper-h6">可儲值方案</h6>
                                <ul class="green-dot-list">
                                    <li>計量型上網方案</li>
                                    <li>計日型上網方案</li>
                                    <li>語音通話方案</li>
                                </ul>
                                <h6 class="paper-h6">儲值優惠</h6>
                                <ul class="check-list mb-3">
                                    <li>儲值語音通話 $300 回饋 500 MB 上網流量</li>
                                    <li>儲值語音通話 $500 回饋 1.2 GB 上網流量</li>
                                    <li>儲值語音通話 $1,000 回饋 2.4 GB 上網流量</li>
                                </ul>
                                <h6 class="paper-h6">儲值步驟</h6>
                                <ul class="step-list">
                                    <li>
                                        <div class="circle">1</div>
                                        <h6>下載【遠傳行動客服APP】</h6>
                                    </li>
                                    <li>
                                        <div class="circle">2</div>
                                        <h6>開啟【遠傳行動客服APP】後，請以易付卡門號與密碼登入</h6>
                                    </li>
                                    <li>
                                        <div class="circle">3</div>
                                        <h6>選擇「上網儲值」或「語音儲值」</h6>
                                    </li>
                                    <li>
                                        <div class="circle">4</div>
                                        <h6>選擇「儲值方案」，再選擇以下方式之一付款：月租帳單、信用卡號、銀行帳號；上網儲值亦可從門號內餘額扣抵</h6>
                                    </li>
                                    <li>
                                        <div class="circle">5</div>
                                        <h6>儲值確認完成後，門號就可上網或撥打使用</h6>
                                    </li>
                                </ul>
                                <section class="fui-section-collapse is-static">
                                    <div class="fui-collapse is-open">
                                        <div role="button" class="collapse-header">注意事項</div>
                                        <div class="collapse-body">
                                            <article>
                                                1.易付出國漫遊上網服務僅適用於4G用戶。
                                                    <br />
                                                    2.自申購成功日起30日內有效，於有效期限內抵達國外當地後開機並確認登錄於指定業者(港澳：Hutchison，新加坡：Starhub)優惠網；收到漫遊上網啟用生效簡訊即開始計算上網時數。
                                                </article>
                                        </div>
                                    </div>
                                </section>`,
                                        },
                                    ],
                                    to: '#',
                                    target: '_blank',
                                    container: false
                                }} />
```

#### Properties

| 名稱         | 屬性   | 選項 | 必填 | 說明 |
| :----------- | :----- | :--- | :--- | :--- |
| title        | string |      |      |      |
| if           | string |      |      |      |
| container    | bool   |      |      |      |
| to           | string |      |      |      |
| collapseList | array  |      |      |      |

```
CollapsePaper2.propTypes = {
  title: PropTypes.string,
  id: PropTypes.string,
  container: PropTypes.bool,
  hideHelpCenter: PropTypes.bool,
  to: PropTypes.string,
  collapseList: PropTypes.arrayOf(
    PropTypes.shape({
      title: PropTypes.string,
      content: PropTypes.string,
      open: PropTypes.bool
    })
  )
}
```

## SectionCollapseInfo

```
import SectionCollapseInfo from '../../components/partials/collapse/SectionCollapseInfo';
<SectionCollapseInfo
  title="貼心小叮嚀"
  content={`
  1.易付出國漫遊上網服務僅適用於4G用戶。<br/>
  2.自申購成功日起30日內有效，於有效期限內抵達國外當地後開機並確認登錄於指定業者(港澳：Hutchison，新加坡：Starhub)優惠網；收到漫遊上網啟用生效簡訊即開始計算上網時數。
`}
/>
```

#### Properties

| 名稱      | 屬性   | 選項 | 必填 | 說明 |
| :-------- | :----- | :--- | :--- | :--- |
| id        | string |      |      |      |
| title     | string |      |      |      |
| className | string |      |      |      |
| content   | string |      |      |      |
| bgColor   | string |      |      |      |
| theme     | string |      |      |      |

## SectionFaq

```
import SectionFaq from '../../components/partials/collapse/SectionFaq';
<SectionFaq {...{
              collapseList: [
                {
                  title: ' 非遠傳電信用戶也可以購買愛講定位手錶嗎?需要搭配門號或續約嗎？可以在那裡買得到？',
                  content: ` 非遠傳電信用戶也可以購買愛講定位手錶嗎?需要搭配門號或續約嗎？可以在那裡買得到？`,
                },
                {
                  title: '遠傳愛講定位手錶所用的SIM卡有限制嗎? 插入非遠傳卡片或不是使用這個方案的SIM卡，手錶還能使用嗎？',
                  content: `遠傳愛講定位手錶所用的SIM卡有限制嗎? 插入非遠傳卡片或不是使用這個方案的SIM卡，手錶還能使用嗎？`,
                },
                {
                  title: '遠傳愛講定位手錶是否支援3G、4G的網路？',
                  content: `遠傳愛講定位手錶是否支援3G、4G的網路？`,
                },
                {
                  title: '遠傳愛講定位手錶能到國外使用嗎？',
                  content: `遠傳愛講定位手錶能到國外使用嗎？`,
                },
                {
                  title: '手錶充飽電需要多久?充飽後能使用多久？',
                  content: `手錶充飽電需要多久?充飽後能使用多久？`,
                },
                {
                  title: '一支手錶可以綁定幾台手機？',
                  content: `一支手錶可以綁定幾台手機？`,
                },
                {
                  title: '更換手機時，需要重新與手錶進行綁定嗎？',
                  content: `更換手機時，需要重新與手錶進行綁定嗎？`,
                },
                {
                  title: '手錶損壞維修方式為何？',
                  content: `手錶損壞維修方式為何？`,
                },
                {
                  title: '產品客服專線、服務時間？',
                  content: `產品客服專線、服務時間？`,
                },
                {
                  title: '如何下載遠傳愛講定位手錶APP？',
                  content: `如何下載遠傳愛講定位手錶APP？`,
                },
              ],
              container: false,
              to: '#',
              target: '_blank'
            }} />
```

#### Properties

| 名稱           | 屬性   | 選項 | 必填 | 說明 |
| :------------- | :----- | :--- | :--- | :--- |
| title          | string |      |      |      |
| id             | string |      |      |      |
| container      | bool   |      |      |      |
| hideHelpCenter | bool   |      |      |      |
| to             | string |      |      |      |
| collapseList   | array  |      |      |      |

```
SectionFaq.propTypes = {
    title: PropTypes.string,
    id: PropTypes.string,
    container: PropTypes.bool,
    hideHelpCenter: PropTypes.bool,
    to: PropTypes.string,
    collapseList: PropTypes.arrayOf(
        PropTypes.shape({
            title: PropTypes.string,
            content: PropTypes.string,
            open: PropTypes.bool
        })
    )
}
```

## SectionFaqTab

```
import SectionFaqTab from '../../components/partials/collapse/SectionFaqTab';
<SectionFaqTab {...{
  title: '常見問題',
  tabs: [
    { label: '申辦門號' },
    { label: '購物' },
    { label: '售後' },
  ],
  collapseList: [
    [
      {
        title: '網路門市申辦攜碼移入生效時間與實體門市之差異?',
        content: '網路門市申辦攜碼移入生效時間與實體門市之差異?',
      },
      {
        title: '我是否可以幫他人在網路門市申辦門號？',
        content: '我是否可以幫他人在網路門市申辦門號？',
      },
      {
        title: '如何查詢申辦進度？',
        content: '如何查詢申辦進度？',
      }
    ],
  ]
}} />
```

#### Properties

| 名稱      | 屬性   | 選項 | 必填 | 說明 |
| :-------- | :----- | :--- | :--- | :--- |
| title     | string |      |      |      |
| helpCenterUrl | string |      |      |      |
| tabs|array    |      |      |      |
|collapseList|array    |      |      |      |

```
SectionFaqTab.propTypes = {
  title: PropTypes.string,
  helpCenterUrl: PropTypes.string,
  tabs: PropTypes.arrayOf(
    PropTypes.shape({
      label: PropTypes.string
    })
  ),
  collapseList: PropTypes.array
};
```

