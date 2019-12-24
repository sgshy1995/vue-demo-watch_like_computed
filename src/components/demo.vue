<template>
    <div>
        <span>目前展示：</span>
        <span class="data">{{user.nickname || user.email || user.phone}}</span>
        <button @click="deleteName">删除昵称</button>
        <button @click="deleteEmail">删除邮箱</button>
        <button @click="deletePhone">删除手机</button>
    </div>
</template>

<script>
export default {
    data(){
        return {
            user:{
                email:'singlesaul@163.com',
                nickname:'eden',
                phone:'13888886666'
            },
            displayname: ''
        }
    },
    watch:{
        'user.email':{
            handler(){
                const {user:{email,nickname,phone}} = this
                this.displayname = nickname || email || phone
            },
            immediate: true
        },
        'user.nickname':{
            handler(){
                const {user:{email,nickname,phone}} = this
                this.displayname = nickname || email || phone
            },
            immediate: true
        },
        'user.phone':{
            handler(){
                const {user:{email,nickname,phone}} = this
                this.displayname = nickname || email || phone
            },
            immediate: true
        }
    },
    methods:{
        deleteName(){
            this.user.nickname = undefined
        },
        deleteEmail(){
            this.user.email = undefined
        },
        deletePhone(){
            this.user.phone = undefined
        }
    }
}
</script>

<style scoped>
button{
    padding: 10px;
    margin: 10px;
    cursor: pointer;
    border-radius: 5px;
    transition: all 0.3s;
}
button:hover{
    transform: scale(1.1);
}
span.data{
    color: brown;
}
</style>