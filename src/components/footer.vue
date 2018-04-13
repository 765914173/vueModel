<template>
  <div class="footer fixed">
      <ul>
          <li><router-link to='/'>Home Page</router-link></li>
          <li><router-link to='/manage'>Management</router-link></li>
      </ul>
  </div>
</template>

<style scoped>
li a{display: inline-block;width: 100%;height:100%;line-height: 100%;text-align: center;}
.footer{width: 300px;height:160px;bottom: 0;margin: 0 auto;}
ul{display: flex;height: 30px;line-height: 30px;width: 100%}
ul li{flex: 1;background-color: #f1f1f1;text-align: center;width: 150px;}
.isIndex li:first-child{background-color: #d3d3d3;}
.isIndex li:first-child a{color: #41b883;}
.isManage li:last-child{background-color: #d3d3d3;}
.isManage li:last-child a{color: #41b883;}
.footer fixed{width: 400px;height: 30px;margin: 0 auto;}
.footer .fixed{height: 500px;}
</style>
