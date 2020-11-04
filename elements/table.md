# Table

## 多重欄位Table

![](../.gitbook/assets/image%20%2889%29.png)

```jsx
<div className="compareTable stick-to-right mt-md-0 mt-3 mb-2">
  <div className="tableLeft">
    <div className="tableHead">
      <table>
        <tbody>
          <tr >
            <td className="align-center is-text-bold is-bg-lightgray70">維修中心</td>
          </tr>
          <tr className='is-bg-white'>
            <td className="align-left pl-3">台大服務中心</td>
          </tr>
          <tr className='is-bg-white'>
            <td className="align-left pl-3">台南服務中心</td>
          </tr>
          <tr className='is-bg-white'>
            <td className="align-left pl-3">高雄建國服務中心</td>
          </tr>
          <tr className='is-bg-white'>
            <td className="align-left pl-3">花蓮中正服務中心</td>
          </tr>
          <tr className='is-bg-white'>
            <td className="align-left pl-3">中壢Nova服務中心</td>
          </tr>
          <tr className='is-bg-white'>
            <td className="align-left pl-3">台中Nova服務中心</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
  <div className="tableRight">
    <div className="tableBody">
      <div className="spaceBox">
        <table className="compareList">
          <tbody>
            <tr className='is-bg-lightgray70'>
              <td className="is-text-bold">
                地址
              </td>
              <td className="is-text-bold">
                電話
              </td>
              <td className="is-text-bold">
                營業時間
              </td>
            </tr>
            <tr className='is-bg-white'>
              <td className="is-text-regular align-left pl-3">
                台北市中正區羅斯福路三段292號3樓
              </td>
              <td className="is-text-regular align-left pl-3 is-text-accent">
                02-2369-0958
              </td>
              <td rowSpan="4" className="is-text-regular align-left pl-3">
                週一~週六 12:00-21:00<br />
                週六僅收件、取件無現場維修。
              </td>
            </tr>
            <tr className='is-bg-white'>
              <td className="is-text-regular align-left pl-3">
                台南市中西區民族路二段231號2樓
              </td>
              <td className="is-text-regular align-left pl-3 is-text-accent">
                06-222-8497
              </td>
            </tr>
            <tr className='is-bg-white'>
              <td className="is-text-regular align-left pl-3">
                高雄市三民區建國二路150號
              </td>
              <td className="is-text-regular align-left pl-3 is-text-accent">
                07-236-1625
              </td>
            </tr>
            <tr className='is-bg-white'>
              <td className="is-text-regular align-left pl-3">
                花蓮市中正路511號3樓
              </td>
              <td className="is-text-regular align-left pl-3 is-text-accent">
                03-8310-735
              </td>
            </tr>
            <tr className='is-bg-white'>
              <td className="is-text-regular align-left pl-3">
                中壢市中正區389號3樓
              </td>
              <td className="is-text-regular align-left pl-3 is-text-accent">
                03-491-9415
              </td>
              <td rowSpan="2" className="is-text-regular align-left pl-3">
                週一~週日 11:00-21:00<br />
                週六、週日僅收件、取件無現場維修。
              </td>
            </tr>
            <tr className='is-bg-white'>
              <td className="is-text-regular align-left pl-3">
                台中市西區英才路506號2樓206櫃位
              </td>
              <td className="is-text-regular align-left pl-3 is-text-accent">
                04-2329-1708
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</div>
```

## 兩欄Table

![](../.gitbook/assets/image%20%28207%29.png)

```jsx
<div className="fui-table-response mb-2 mb-lg-4">
    <table className="confirm-table">
      <tbody>
        <tr>
          <th>方案</th>
          <td>多國家上網吃到飽</td>
        </tr>
        <tr>
          <th>適用國家</th>
          <td>請查看</td>
        </tr>
        <tr>
          <th>使用期間</th>
          <td>2020/05/26 17:30 - 2020/05/30 17:30 </td>
        </tr>
        <tr>
          <th>天數</th>
          <td>4 天</td>
        </tr>
        <tr>
          <th>預估費用</th>
          <td>請以實際出帳金額為主</td>
        </tr>
      </tbody>
    </table>
  </div>
```



