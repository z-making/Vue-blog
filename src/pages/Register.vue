<template>
  <div id="register">
    <h4>用户名</h4>
    <input v-model="username" placeholder="请输入用户名">
    <h4>密码</h4>
    <input v-model="password" type="password" placeholder="请输入密码" @keyup.enter="onRegister">
    <el-button @click="onRegister">立即注册</el-button>
    <p>已有账号？<router-link to="/login">立即登录</router-link></p>
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
      'register'
    ]),
    onRegister(){
      this.register({username:this.username,password:this.password})
      .then(()=>{
        this.$router.push({path:'/'})
      })
    }
  }
}
</script>

<style lang="less">
@import "../assets/base.less";

#register{
  display: grid;
  justify-content: center;
  padding-top: 40px;

  input{
    width: 400px;
    height: 40px;
  }

  button{
    width: 100px;
    margin-top: 30px;
    border: 1px solid green;
    color: green;
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