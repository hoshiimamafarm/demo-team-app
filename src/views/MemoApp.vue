<template>
  <h1>Vue メモ</h1>
  <div class="memo-list">
    <ul class="memo-list__container">
      <memoOutput
        v-for="(memo, index) in memos"
        v-bind:key="index"
        class="memo"
        v-bind:memo="memo"
        v-bind:index="index"
      ></memoOutput>
    </ul>
    <div class="add-memo-field">
      <input class="add-memo-field__input" type="text" v-model="textMemo" />
      <button v-on:click="addButton" class="add-memo-field__button">
        追加
      </button>
    </div>
  </div>
</template>

<script>
import MemoOutput from "@/components/MemoOutput.vue"
export default {
  components: {
    memoOutput: MemoOutput,
  },
  data() {
    return {
      textMemo: " ",
      memos: [],
    }
  },
  methods: {
    addButton: function () {
      this.memos.push({
        text: this.textMemo,
      })
    },
  },
}
</script>

<style scoped>
.memo-list {
  padding-left: 5rem;
  padding-right: 5rem;
  display: flex;
  flex-direction: column;
  align-items: stretch;
  max-width: 512px;
  margin-left: auto;
  margin-right: auto;
}

.memo-list__container {
  padding: 0;
}

/* .memo {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.5rem;
  border-radius: 5px;
}

.memo:hover {
  color: white;
  background-color: #b23b61;
} */

.add-memo-field {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.add-memo-field__input {
  padding: 10px;
}
.add-memo-field__button {
  padding: 0.5rem 0.5rem;
  border: solid 1px black;
  border-radius: 5px;
  background-color: white;
}

.add-memo-field__button:hover {
  background-color: #b2ae3b;
  border-radius: 5px;
}

/* .memo__text {
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
} */
</style>
