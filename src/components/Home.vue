<template>
<v-container>
  <v-layout row wrap>
    <v-flex xs12 text-center>
      <h1>TODO List</h1>
				<p>전체 할 일: {{todoList.length}}개 / 완료된 할 일: {{countDone}}개 / 남은 할 일:{{todoList.length - countDone}}개 </p>
    </v-flex>
    <v-flex xs6 pa-2>
      <List
        :todoList="todoList"
        @statusControl="statusControl"
        @listDelete="listDelete"
      />
    </v-flex>
    <v-flex xs6 pa-2>
      <ListAdd
        @listAdd="listAdd"
        @listEdit="listEdit"
      />
    </v-flex>
  </v-layout>
</v-container>
</template>

<script>
import List from "./List"
import ListAdd from "./ListAdd"

export default {
  components: {
    List,
    ListAdd
  },
  data() {
    return {
      todoList: []
    }
  },
  computed: {
    countDone() {
      let count = 0
      this.todoList.forEach(list => {
        if(list.status === "done")
        count++
      })
      return count
    }
  },
  methods: {
    listAdd(memo) {
      this.todoList.push({memo: memo, status: "created"})
    },
    statusControl(index, status) {
      this.todoList[index].status = status
    },
    listDelete(index) {
      this.todoList.splice(index, 1) // 찾은 인덱스부터 1개 지우기
    },
    listEdit(memo, index) {
      this.todoList[index].memo = memo
    }
  }
}
</script>
