<template>
  <div>
    <h2>你好，{{ user.uname }}</h2>
    <el-button @click="logout"> 登出 </el-button>
    <div class="unity-iframe">
      <iframe src="../../../static/index.html" frameborder="0" width="1024px" height="600px"></iframe>
    </div>
    
  </div>
</template>

<script>
export default {
  data() {
    return {
      user: {
        uname: "",
        uid: null,
      },
    };
  },
  methods: {
    logout(){
      // 移除本地用户登录信息
      sessionStorage.removeItem('userInfo');
      // 跳转页面到登录页
      this.$router.push('/login');
    }
  },
  mounted() {
    if (sessionStorage.getItem('userInfo')) {
      // 将用户信息存储到sessionStorage中
      this.user = JSON.parse(sessionStorage.getItem('userInfo'));
    }
  },
};
</script>


<style scoped>

.unity-iframe{
 position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

</style>