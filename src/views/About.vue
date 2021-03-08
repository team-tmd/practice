<template>
  <div id="app">
    <div class="main-container">
      <div class="list-container">
        <input
          class="input-box"
          type="text"
          v-model="memo_input"
          v-on:keyup.enter="AddMemo"
        />
        <button class="button-input" v-on:click="AddMemo">New</button>
        <div
          class="cards"
          v-for="(memo_state, index) in memo_array"
          v-bind:key="index"
        >
          <!--ここに追加されていく-->
          <label v-bind:class="{ done: memo_state.isDone }">
            <input
              type="checkbox"
              v-model="memo_state.isDone"
              v-on:click="DoneMemo(memo_state)"
            />
            {{ memo_state.text }}
          </label>
          <div class="delete" v-on:click="DeleteMemo(memo_state)"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      //変数や配列など
      memo_input: "",
      memo_array: [
        {
          text: "背中トレ", //m.text
          isDone: false, //m.isDone
        },
        {
          text: "肩トレ", //m.text
          isDone: false, //m.isDone
        },
        {
          text: "腕トレ", //m.text
          isDone: false, //m.isDone
        },
        {
          text: "脚トレ", //m.text
          isDone: false, //m.isDone
        },
      ],
      done_memo_array: [{ done_text: "胸トレ" }],
    }
  },
  methods: {
    //関数など
    AddMemo: function() {
      if (this.memo_input != "") {
        const obj = { text: this.memo_input, isDone: false }
        this.memo_array.push(obj)
        this.memo_input = ""
      }
    },
    DeleteMemo: function(memo_state) {
      this.memo_array.splice(this.memo_array.indexOf(memo_state), 1)
      this.memo_array = this.memo_array.filter(function(memo_state) {
        return memo_state.isDone === false
      })
    },
    DoneMemo: function(memo_state) {
      this.done_memo_array.push({ done_text: memo_state.text })
      //this.memo_array = this.memo_array.filter(function(memo_state) {
      //return memo_state.isDone === false
      //})
    },
  },
}
</script>

<style scoped>
#app {
  height: 100vh;
  background-color: black;
}

.input-box {
  margin-top: 5px;
  margin-left: 2px;
  color: white;
  background-color: black;
  border-radius: 5px;
  border: 1px solid white;
}
.button-input {
  color: white;
  background-color: black;
  border-radius: 5px;
  border: 1px solid white;
}
.button-input:hover {
  color: black;
  background-color: white;
}

.main-container {
  display: flex;
  flex-flow: row;
}

.cards {
  width: 350px;
  margin-top: 4px;
  position: relative;
  padding: 4px;
  color: rgb(255, 0, 149);
  border-radius: 5px;
  border: 1px solid rgb(255, 0, 149);
}
.cards:hover {
  box-shadow: inset 0px 0px 10px 5px rgb(255, 0, 149);
}
.done {
  color: rgb(255, 0, 149);
  text-decoration: line-through;
}
.delete {
  position: absolute;
  bottom: 4px;
  opacity: 0.5;
  z-index: 16px;
  right: 4px;
}
.cards:hover .delete:after {
  content: "×";
}
.cards:hover .delete:hover {
  opacity: 1;
}

.done-list {
  margin-top: 28px;
  margin-left: 30px;
}
.done-cards {
  width: 350px;
  margin-top: 4px;
  position: relative;
  padding: 4px;
  color: rgb(217, 255, 0);
  border-radius: 4px;
  border: 1px solid rgb(217, 255, 0);
}
.done-cards:hover {
  box-shadow: inset 0px 0px 10px 5px rgb(217, 255, 0);
}
</style>
