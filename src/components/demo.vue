<template>
  <div>
    <h1>Vue</h1>
    <hr>
    <h3>watch 模拟 computed，以及 watch 的 deep 和 immediate</h3>
    <hr>
    <span>目前展示：</span>
    <span class="data">{{user.nickname || user.email || user.phone}}</span>
    <button @click="deleteName">删除昵称</button>
    <button @click="deleteEmail">删除邮箱</button>
    <button @click="deletePhone">删除手机</button>
    <hr>
    <span>Obj1:</span>
    <span class="property">a=</span>
    <span class="data">{{obj1.a}}</span>
    <span>（没有deep）</span>
    <button @click="obj1.a += 1">控制台看我变化</button>
    <span>Obj2:</span>
    <span class="property">b=</span>
    <span class="data">{{obj2.b}}</span>
    <span>（有deep）</span>
    <button @click="obj2.b += 1">控制台看我变化</button>
  </div>
</template>

<script>
// eslint-disable-next-line no-unused-vars
import { deeppink } from "color-name";
export default {
  data() {
    return {
      user: {
        email: "singlesaul@163.com",
        nickname: "eden",
        phone: "13888886666"
      },
      obj1: {
        a: 0
      },
      obj2: {
        b: 0
      },
      displayname: ""
    };
  },
  watch: {
    "user.email": {
      handler() {
        const {
          user: { email, nickname, phone }
        } = this;
        this.displayname = nickname || email || phone;
      },
      immediate: true
    },
    "user.nickname": {
      handler() {
        const {
          user: { email, nickname, phone }
        } = this;
        this.displayname = nickname || email || phone;
      },
      immediate: true
    },
    "user.phone": {
      handler() {
        const {
          user: { email, nickname, phone }
        } = this;
        this.displayname = nickname || email || phone;
      },
      immediate: true
    },
    obj1() {
      console.log("obj1 变了");
    },
    "obj1.a": () => {
      console.log("obj1 的 a 变了");
    },
    obj2:{
        handler:()=>{
            console.log('obj2 变了')
        },
        deep: true
    },
    "obj2.b": () => {
        console.log("obj2 的 b 变了");
      }
  },
  methods: {
    deleteName() {
      this.user.nickname = undefined;
    },
    deleteEmail() {
      this.user.email = undefined;
    },
    deletePhone() {
      this.user.phone = undefined;
    }
  }
};
</script>

<style scoped>
button {
  padding: 10px;
  margin: 10px;
  cursor: pointer;
  border-radius: 5px;
  transition: all 0.3s;
  border: 1px solid black;
}
button:focus{
    outline: none;
}
button:hover {
  transform: scale(1.1);
}
span{
    margin: 5px;
}
span.data {
  color: brown;
}
span.property{
    color: aqua;
}
</style>