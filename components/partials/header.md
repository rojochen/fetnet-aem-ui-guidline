# header

## MenuDrawer

```
let menuItem = [
        {
          title: '商品',
          list: [
            {
              icon: '/resources/common/menu-icon/phone.svg',
              iconActive: '/resources/common/menu-icon/phone-active.svg',
              text: '商品',
              list: [
                { link: '/', text: '手機', },
                { link: '/', text: '平板、3C' },
                { link: '/', text: '智慧家電', },
                { link: '/', text: '配件', },
                { link: '/', text: '出國上網卡', },
              ]
            },
            {
              icon: '/resources/common/menu-icon/application.svg',
              iconActive: '/resources/common/menu-icon/application-active.svg',
              text: '行動應用',
              list: [
                { link: '#', text: '手機保險', },
                { link: '#', text: 'Bobee 守護寶', },
                { link: '#', text: '愛講定位手錶', },
                { link: '#', text: '遠傳全能行動管家', },
                { link: '#', text: '一號多機', },
                { link: '#', text: 'MMS/簡訊服務', },
              ],
            },
            {
              icon: '/resources/common/menu-icon/entertament.svg',
              iconActive: '/resources/common/menu-icon/entertament-active.svg',
              text: '數位・加值服務',
              list: [
                { link: '/', text: 'friDay 影音' },
                { link: '/', text: 'friDay 音樂' },
                { link: '/', text: 'friDay 購物' },
                { link: '/', text: 'friDay 相片書' },
                { link: '/', text: 'friDay 57' },
                { link: '/', text: 'friDay 來電答鈴' },
              ]
            }
          ],
        },
        {
          title: '資費',
          list: [
            {
              icon: '/resources/common/menu-icon/online-plan.svg',
              iconActive: '/resources/common/menu-icon/online-plan-active.svg',
              text: '網路限定',
              list: [
                { link: '/', text: '$499 飆網吃到飽' },
                { link: '/', text: '$149 輕速雙飽' },
                { link: '/', text: '$199 夠用最實在' },
                { link: '/', text: '$399 網內飽 + 夯機 $0' },
                { link: '/', text: '$399 吃到飽 + 夯機 $0' },
                { link: '/', text: '推薦續約' },
              ]
            },
            {
              icon: '/resources/common/menu-icon/main-plan.svg',
              iconActive: '/resources/common/menu-icon/main-plan-active.svg',
              text: '主要資費',
              list: [
                { link: '/', text: '4.5G 資費' },
                { link: '/', text: '預付卡' },
                { link: '/', text: '國際電話' },
                { link: '/', text: 'Wi-Fi 上網' },
              ]
            },
            {
              icon: '/resources/common/menu-icon/travel-wifi.svg',
              iconActive: '/resources/common/menu-icon/travel-wifi-active.svg',
              text: '出國/來台上網',
              list: [
                { link: '/', text: '月租用戶原號漫遊' },
                { link: '/', text: '想去哪？就搜哪！' },
                { link: '/', text: '預付卡原號漫遊' },
                { link: '/', text: '出國神卡 - 遠遊卡' },
                { link: '/', text: '來台旅客上網卡' },
                { link: '/', text: '漫遊開關設定' },
                { link: '/', text: '機上漫遊' },
              ]
            },
            {
              icon: '/resources/common/menu-icon/home-wifi.svg',
              iconActive: '/resources/common/menu-icon/home-wifi-active.svg',
              text: '家用上網',
              list: [
                { link: '/', text: '遠傳大無線' },
                { link: '/', text: '遠傳大寬頻光纖' },
              ]
            },
          ],
        },
        {
          title: '遠傳生活圈',
          list: [
            {
              icon: '/resources/common/menu-icon/topic.svg',
              iconActive: '/resources/common/menu-icon/topic-active.svg',
              text: '主題策展',
              list: [
                { link: '/', text: '生活圈策展' },
                { link: '/', text: '異鄉遊子' },
                { link: '/', text: '追劇人生' },
                { link: '/', text: '斜槓老爸' },
                { link: '/', text: '樂活自在' },
              ]
            },
            {
              icon: '/resources/common/menu-icon/lifestyle.svg',
              iconActive: '/resources/common/menu-icon/lifestyle-active.svg',
              text: '我的生活圈',
              list: [
                { link: '/', text: '我的遠傳幣' },
                { link: '/', text: '會員等級說明' },
                { link: '/', text: '白金會員生活禮' },
              ]
            },
          ],
        },
        {
          title: '個人專區',
          list: [
            {
              icon: '/resources/common/menu-icon/pay.svg',
              iconActive: '/resources/common/menu-icon/pay-active.svg',
              text: '帳單/繳費',
              list: [
                {
                  text: '帳單服務',
                  list: [
                    { link: '/', text: '本期應繳金額' },
                    { link: '/', text: '未結帳金額/上網用量' },
                    { link: '/', text: '繳費/代收交易/發票查詢' },
                    { link: '/', text: '4G上網用量加購' },
                    { link: '/', text: '帳單代收設定/額度管理' },
                    { link: '/', text: '4G即時用量查詢' },
                  ]
                },
                {
                  text: '繳費服務',
                  list: [
                    { link: '/', text: '線上繳費' },
                    { link: '/', text: '銀行帳號繳費' },
                    { link: '/', text: '信用卡繳費' },
                    { link: '/', text: '手機條碼繳費' },
                  ]
                },
                {
                  text: '帳單通知設定',
                  list: [
                    { link: '/', text: '帳務及繳費通知設定' },
                    { link: '/', text: '「合併帳單」申請' },
                  ]
                },
              ]
            },
            {
              icon: '/resources/common/menu-icon/contract.svg',
              iconActive: '/resources/common/menu-icon/contract-active.svg',
              text: '合約費率',
              list: [
                { link: '/', text: '目前費率查詢' },
                { link: '/', text: '費率異動/變更' },
                { link: '/', text: '推薦費率查詢' },
                { link: '/', text: '合約資訊查詢' }
              ]
            },
            {
              icon: '/resources/common/menu-icon/global.svg',
              iconActive: '/resources/common/menu-icon/global-active.svg',
              text: '漫遊與門號服務',
              list: [
                {
                  text: '出國漫遊',
                  list: [
                    { link: '/', text: '漫遊通話/上網設定' },
                    { link: '/', text: '漫遊上網包申辦' },
                    { link: '/', text: '7日/15日漫遊優惠申請' },
                    { link: '/', text: '漫遊上網用量查詢' },
                    { link: '/', text: '漫遊加購記錄' },
                    { link: '/', text: '漫遊旅遊包購買記錄' },
                  ]
                },
                {
                  text: '門號功能設定',
                  list: [
                    { link: '/', text: '來電答鈴' },
                    { link: '/', text: '來電過濾' },
                    { link: '/', text: '停車費代收設定' },
                  ]
                },
              ]
            },
            {
              icon: '/resources/common/menu-icon/history.svg',
              iconActive: '/resources/common/menu-icon/history-active.svg',
              text: '交易/異動記錄',
              list: [
                {
                  link: '/',
                  text: '停車費代收記錄查詢'
                },
              ]
            },
            {
              icon: '/resources/common/menu-icon/prepaid.svg',
              iconActive: '/resources/common/menu-icon/prepaid-active.svg',
              text: '預付卡專區',
              list: [
                {
                  text: '儲值/加購',
                  list: [
                    { link: '/', text: '通話金儲值' },
                    { link: '/', text: '上網儲值' },
                    { link: '/', text: '儲值卡儲值' },
                    { link: '/', text: '漫遊上網加購' },
                  ]
                },
                {
                  text: '交易/記錄查詢',
                  list: [
                    { link: '/', text: '餘額/上網/到期日查詢' },
                    { link: '/', text: '儲值交易查詢' },
                    { link: '/', text: '預付卡加購交易查詢' },
                    { link: '/', text: '發票記錄查詢' },
                    { link: '/', text: '小額代收/網路門市交易查詢' },
                  ]
                },
              ]
            },
            {
              icon: '/resources/common/menu-icon/member-cbu.svg',
              iconActive: '/resources/common/menu-icon/member-cbu-active.svg',
              text: '帳戶服務',
              list: [
                {
                  link: '/',
                  text: '我的訂單'
                },
                {
                  text: '帳戶管理',
                  list: [
                    { link: '/', text: '個人資料維護' },
                    { link: '/', text: '快速登入設定' },
                    { link: '/', text: '密碼變更' },
                    { link: '/', text: '付款工具維護' },
                    { link: '/', text: '電子發票設定' },
                    { link: '/', text: '更改手機號碼' },
                    { link: '/', text: '訂閱電子報' },
                    { link: '/', text: '已領取序號查詢' },
                  ]
                },
                {
                  text: 'Happy Go 優惠',
                  list: [
                    { link: '/', text: 'Happy Go 點數' },
                    { link: '/', text: 'Happy Go 折抵' },
                    { link: '/', text: 'Happy Go 折抵記錄查詢' },
                  ]
                },
              ]
            },
          ],
        },
        {
          title: '幫助中心',
          list: [
            {
              icon: '/resources/common/menu-icon/help-center.svg',
              iconActive: '/resources/common/menu-icon/help-center-active.svg',
              text: '常見問題',
              list: [
                { link: '/', text: '幫助中心首頁' },
                { link: '/', text: '帳單/繳費/合約' },
                { link: '/', text: '網路購物與商品' },
                { link: '/', text: '遠傳生活圈' },
                { link: '/', text: '月租型' },
                { link: '/', text: '其他常見問題' },
              ]
            },
            {
              icon: '/resources/common/menu-icon/store-service.svg',
              iconActive: '/resources/common/menu-icon/store-service-active.svg',
              text: '門市服務',
              list: [
                { link: '/', text: '找門市' },
                { link: '/', text: '門市預約及查詢' },
                { link: '/', text: '預約門市換號' },
                { link: '/', text: '服務申請證件提醒' }
              ]
            },
            {
              icon: '/resources/common/menu-icon/customer.svg',
              iconActive: '/resources/common/menu-icon/customer-active.svg',
              text: '客服中心',
              list: [
                { link: '/', text: '客服信箱' },
                { link: '/', text: '服務公告' },
                { link: '/', text: '行動客服 APP' }
              ]
            },
            {
              icon: '/resources/common/menu-icon/information-learning.svg',
              iconActive: '/resources/common/menu-icon/information-learning-active.svg',
              text: '資訊學習',
              list: [
                { link: '/', text: '手機/平板操作說明' },
                { link: '/', text: '免費學習課程' },
                { link: '/', text: 'APP 總覽' }
              ]
            },
            {
              icon: '/resources/common/menu-icon/fix.svg',
              iconActive: '/resources/common/menu-icon/fix-active.svg',
              text: '維修保固',
              list: [
                { link: '/', text: '保固查詢' },
                { link: '/', text: '網路預約報修' },
                { link: '/', text: '網路預約報修查詢' },
                { link: '/', text: '維修進度查詢' },
              ]
            },
            {
              icon: '/resources/common/menu-icon/other.svg',
              iconActive: '/resources/common/menu-icon/other-active.svg',
              text: '其他服務',
              list: [
                { link: '/', text: '網內外門號查詢' },
                { link: '/', text: '電信特殊號碼查詢' },
                { link: '/', text: '網路涵蓋率查詢' },
                { link: '/', text: '固網電子帳單' },
                { link: '/', text: '寬頻服務' },
              ]
            },
          ],
        },
        {
          title: '5G',
          link: '#',
        }
      ]
import MenuDrawer from './MenuDrawer';
<MenuDrawer
  id={`navigationMobile-${i + 3}`}
  {...menuItem}
  closeDrawer={(e) => toggleMenu(i)}
  closeMenu={(e) => {
    toggleMenu(i);
    openMenu();
  }}
/>
```

#### Properties

| 名稱      | 屬性   | 選項 | 必填 | 說明 |
| :-------- | :----- | :--- | :--- | :--- |
| title     | string |      |      |      |
| list     | array |      |      |      |
|closeDrawer     | func |      |      |      |
|closeMenu     | func |      |      |      |

```
MenuDrawer.propTypes = {
  title: PropTypes.string,
  list: PropTypes.arrayOf(
    PropTypes.shape({
      title: PropTypes.string,
      icon: PropTypes.string,
      child: PropTypes.arrayOf(
        PropTypes.shape({
          text: PropTypes.string,
          link: PropTypes.string,
          child: PropTypes.arrayOf(
            PropTypes.shape({
              text: PropTypes.string,
              link: PropTypes.string,
            })
          ),
        })
      ),
    })
  ),
  closeDrawer: PropTypes.func,
  closeMenu: PropTypes.func,
};
```
