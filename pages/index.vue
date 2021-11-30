<template>
  <div>
    <h2>Asana クローン</h2>
    <div class="addArea">
      <input type="text" name="addName" id="addName" />
      <button id="addButton">追加</button>
    </div>
    <table class="Lists">
      <thead>
        <tr>
          <th>タスク</th>
          <th>登録日時</th>
          <th>状態</th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>テスト</td>
          <td>2020-04-30 17:00</td>
          <td><button class="button button--yet">作業前</button></td>
          <td><button class="button button--delete">削除</button></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {}
</script>
