# PanelContent

## PanelButton

```
import PanelButton from '../components/panelContent/PanelButton';
<PanelButton link='#' text='手機' />
```

#### Properties

| 名稱      | 屬性   | 選項 | 必填 | 說明 |
| :-------- | :----- | :--- | :--- | :--- |
| btnStyle  | string |      |      |      |
| text      | string |      | true |      |
| link      | string | true |      |      |
| className | string |      |      |      |
| target    | string |      |      |      |


## PanelFigure1

```
import PanelFigure1 from '../../components/panelContent/PanelFigure1';
<PanelFigure1 inline={false} image={item.img} caption={item.name} />
```

#### Properties

| 名稱        | 屬性   | 選項 | 必填 | 說明 |
| :---------- | :----- | :--- | :--- | :--- |
| inline      | bool   |      |      |      |
| retinaImage | string |      |      |      |
| image       | string |      | true |      |
| caption     | string |      |      |      |
| maxWidth    | number |      |      |      |

## PanelFigure2

```
import PanelFigure2 from '../../components/panelContent/PanelFigure2';
<PanelFigure2
  key={i}
  figures={item.figures}
  column={item.column}
/>
```

#### Properties

| 名稱      | 屬性   | 選項 | 必填 | 說明 |
| :-------- | :----- | :--- | :--- | :--- |
| title     | string |      |      |      |
| content   | string |      |      |      |
| className | string |      |      |      |

## PanelInformation

```
import PanelInformation from '../../components/panelContent/PanelInformation';
<PanelInformation
  className="py-0"
  title={`<h5 class="m-0 is-text-black50 is-text-medium">撥打限制須知</h5>`}
  content={`
    <h6 class="m-0 is-text-regular">設定指定轉接後，所有來話一經轉接到您設定的電話號碼時，轉接費用必須由您支付。</h6>
    <ol class="order-list mb-0">
        <li>
            <span class="decimal">1</span>
            設定通話限制功能時，則指定轉接功能將無法設定（指定轉接視同是由客戶手機撥出電話，若已設定禁撥電話的通話限制，則客戶無法撥出任何電話，因此無法設定指定轉接）。
        </li>
        <li>
            <span class="decimal">2</span>
            若設定禁撥及禁接來話，簡訊服務將一併限制。
        </li>
        <li>
            <span class="decimal">3</span>
            此功能免費，使用前請洽客服中心開啟功能。
        </li>
    </ol>`}
/>
```

#### Properties

| 名稱      | 屬性   | 選項 | 必填 | 說明 |
| :-------- | :----- | :--- | :--- | :--- |
| title     | string |      | true |      |
| date      | string |      |      |      |
| className | string |      |      |      |
| content   | string |      | true |      |


## PanelLayout

```
import PanelLayout from '../../components/panelContent/PanelLayout'
<PanelLayout
  key={i}
  imageWidth={item.img.width}
  image={item.img.url}
  alt={item.img.alt}
  title={item.title}
  content={item.content}
  contentPosition={item.contentPosition}
>
</PanelLayout>
```

#### Properties

| 名稱      | 屬性   | 選項 | 必填 | 說明                                                                                                                                                       |
| :-------- | :----- | :--- | :--- | :--------------------------------------------------------------------------------------------------------------------------------------------------------- |
| title     | string |      |      |                                                                                                                                                            |
| bgColor   | string |      |      |                                                                                                                                                            |
| initial   | bool   |      |      |                                                                                                                                                            |
| content   | string |      |      |                                                                                                                                                            |
| className | string |      |      |                                                                                                                                                            |
| data      | array  |      |      | title: PropTypes.string,width: PropTypes.string,image: PropTypes.string,alt: PropTypes.string,content: PropTypes.string,contentPosition: PropTypes.string, |

## PanelList
```
import PanelList from '../panelContent/PanelList'
<PanelList
  prefix='number'
  list={[
    { text: '連續三次輸入PIN1碼錯誤，SIM卡會自動上鎖，系統會暫時中止各項服務。' },
    { text: '連續三次輸入PIN2碼錯誤，此時與PIN2碼相關之功能將無法使用，您仍可正常收發話。' }
  ]}
/>
```

#### Properties

| 名稱      | 屬性   | 選項 | 必填 | 說明 |
| :-------- | :----- | :--- | :--- | :--- |
| prefix    | string |      | true |      |
| className | string |      |      |      |
| list      | array  |      | true |      |


## PanelTab

```
import PanelTab from '../../components/panelContent/PanelTab';
<PanelTab
  tabs={{
    name: 'panel-tab',
    list: [
      { name: 'panel-tab-1', label: '單國漫遊' },
      { name: 'panel-tab-2', label: '多國漫遊' },
      { name: 'panel-tab-3', label: '機上漫遊' },
    ],
  }}>
  <Panel>
  ..content
  </Panel>
<PanelTab />
```

#### Properties

| 名稱       | 屬性   | 選項 | 必填 | 說明                                         |
| :--------- | :----- | :--- | :--- | :------------------------------------------- |
| className  | string |      |      |                                              |
| tabs       | array  |      |      | name: PropTypes.string,list: PropTypes.array |
| activeTab  | number |      |      |                                              |
| onClick    | func   |      |      |                                              |
| tabContent | arry   |      |      | content: PropTypes.string                    |


## PanelTable

```
import PanelTable from '../../components/panelContent/PanelTable';
<PanelTable
  content={`<div class="compareTable content-16 clearfix">
      <div class="tableLeft">
          <div class="tableHead">
              <table>
                  <tbody>
                      <tr style="height: 66px;">
                          <th></th>
                      </tr>
                      <tr style="height: 66px;">
                          <th>加總網路流量</th>
                      </tr>
                      <tr style="height: 66px;">
                          <th>基本網路流量</th>
                      </tr>
                      <tr style="height: 66px;">
                          <th>贈送網路流量</th>
                      </tr>
                      <tr style="height: 66px;">
                          <th>使用期限</th>
                      </tr>
                  </tbody>
              </table>
          </div>
      </div>
      <div class="tableRight">
          <div class="tableBody">
              <div class="spaceBox">
                  <table class="compareList">
                      <tbody>
                          <tr style="height: 66px;">
                          <td>羽量版</td>
                          <td>輕量版</td>
                          <td>基本版</td>
                          <td>重量版</td>
                          <td>巨量版</td>
                          </tr>
                          <tr style="height: 66px;">
                          <td>2 GB <span style="text-decoration:line-through">1.2 GB</span></td>
                          <td>4 GB <span style="text-decoration:line-through">2.2 GB</span></td>
                          <td>10 GB <span style="text-decoration:line-through">5 GB</span></td>
                          <td>16 GB <span style="text-decoration:line-through">8 GB</span></td>
                          <td>20 GB</td>
                          </tr>
                          <tr style="height: 66px;">
                          <td>180 MB</td>
                          <td>300 MB</td>
                          <td>699 MB</td>
                          <td>4096 MB</td>
                          <td>5 GB</td>
                          </tr>
                          <tr style="height: 66px;">
                          <td>1048.8 MB</td>
                          <td>1966.8 MB</td>
                          <td>4421 MB</td>
                          <td>4096 MB</td>
                          <td>15 GB</td>
                          </tr>
                          <tr style="height: 66px;">
                          <td>60日</td>
                          <td>60日</td>
                          <td>98日</td>
                          <td>185日</td>
                          <td>120日</td>
                          </tr>
                      </tbody>
                  </table> 
              </div>
          </div>
      </div>
  </div>`
  }
/>
```

#### Properties

| 名稱    | 屬性   | 選項 | 必填 | 說明 |
| :------ | :----- | :--- | :--- | :--- |
| content | string |      | true |      |

## PanelTitle1

```
import PanelTitle1 from '../components/panelContent/PanelTitle1';
<PanelTitle1 title='商品' />
```

#### Properties

| 名稱  | 屬性   | 選項 | 必填 | 說明 |
| :---- | :----- | :--- | :--- | :--- |
| title | string |      | true |      |
