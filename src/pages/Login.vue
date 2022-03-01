<template>
  <div id="login">
    <h4>用户名</h4>
    <input v-model="username"  placeholder="用户名">
    <h4>密码</h4>
    <input v-model="password" type="password" placeholder="密码" @keyup.enter="onLogin">
    <el-button @click="onLogin" >立即登录</el-button>
    <p>没有账号?<router-link to="/register">注册新用户</router-link></p>
  </div>
</template>

<script>
import {mapActions} from 'vuex'
export default {
  data(){
    return{
      username:'',
      password:''
    }
  },
  methods:{
    ...mapActions([
      'login'
    ]),
    onLogin(){
      this.login({username:this.username,password:this.password})
      .then(()=>{
        this.$router.push({path:this.$route.query.redirect || '/'})
      })
    }
  }
}
</script>

<style lang="less">

@import "../assets/base.less";

#login{
    display: grid;
    justify-content: center;
    padding-top: 40px;

    input{
      width: 400px;
      height: 40px;
    }

    button{
      margin-top: 30px;
      width: 100px;
      color: green;
      border: 1px solid green;
    }

    p{
      text-align: center;
      font-size: 12px;
      color: @textLighterColor;
      
      a{
        color: @themeColor;
      }
    }


}
</style>