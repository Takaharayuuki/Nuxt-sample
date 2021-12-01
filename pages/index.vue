<template>
  <div>
    <h2>Asana Clone</h2>
    <div class="addArea">
      <input v-model="content" type="text" name="addName" id="addName" />
      <button @click="insert" id="addButton">セクションを追加</button>
      <button @click="insert" id="addButton">タスクを追加</button>
    </div>
    <div class="Filter">
      <button class="button button--gray is-active" @click="flag_reset">
        全て
      </button>
      <button class="button button--gray" @click="find('作業前')">
        作業前
      </button>
      <button class="button button--gray" @click="find('作業中')">
        作業中
      </button>
      <button class="button button--gray" @click="find('完了')">完了</button>
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
        <tr v-for="(item, index) in display_todos" :key="index">
          <td>{{ item.content }}</td>
          <td>{{ item.created }}</td>
          <td>
            <button class="button button--yet" @click="changeState(item)">
              {{ item.state }}
            </button>
          </td>
          <td>
            <button class="button button--delete" @click="remove(item)">
              削除
            </button>
          </td>
        </tr>
        <tr v-for=""></tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import { mapState } from 'vuex'

export default {
  data() {
    return {
      content: '',
      find_state: '',
      find_flg: false,
    }
  },
  methods: {
    insert() {
      if (this.content != '') {
        this.$store.commit('insert', { content: this.content })
        this.content = ''
      }
    },
    remove(todo) {
      this.$store.commit('remove', todo)
    },
    changeState(todo) {
      this.$store.commit('changeState', todo)
    },
    find(findState) {
      this.find_state = findState
      this.find_flg = true
    },
    flag_reset() {
      this.find_flg = false
    },
  },
  computed: {
    ...mapState(['todos']),

    display_todos() {
      if (this.find_flg) {
        let arr = []
        let data = this.todos
        data.forEach((element) => {
          if (element.state == this.find_state) {
            arr.push(element)
          }
        })
        return arr
      } else {
        return this.todos
      }
    },
  },
}
</script>
