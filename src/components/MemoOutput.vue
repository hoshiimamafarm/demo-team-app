<template>
  <li class="memo">
    <div class="memo__checkbox">
      <input type="checkbox" v-model="isDone" />
    </div>
    <div v-if="isDone" class="memo__text memo__text--done">
      {{ index }}:{{ memo.text }}
    </div>
    <div v-else class="memo__text">{{ index }}:{{ memo.text }}</div>
    <button v-on:click="deleteButton(index)" class="memo__delete">削除</button>
  </li>
</template>

<script>
export default {
  props: ["memo", "index"],
  data() {
    return {
      isDone: false,
    }
  },
  methods: {
    //deleteButtonが押されたらmemoが消える
    //押されたdeleteButtonのindexをMemoApp.vueに伝える
    //MemoApp.vueでmemoを消す
    deleteButton: function (index) {
      this.$emit("onclick", index)
    },
  },
}
</script>

<style>
.memo {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.5rem;
  border-radius: 5px;
}

.memo:hover {
  color: white;
  background-color: #b23b61;
}
.memo__text {
  margin-left: 2rem;
  text-align: left;
}

.memo__text--done {
  text-decoration-line: line-through;
}

.memo__delete {
  margin-left: 1rem;
  padding: 0.5rem 0.5rem;
  border: solid 1px black;
  border-radius: 5px;
  background-color: white;
}

.memo__delete:hover {
  background-color: #b2ae3b;
  border-radius: 5px;
}
</style>
