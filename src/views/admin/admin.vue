<template>
  <div>
    <el-container direction="vertical">
      <el-header id="header" height="100px">
        <div id="exit">
          <el-button type="text" @click="hrefExit">退出登录</el-button>
        </div>
      </el-header>

      <el-aside id="aside-left" width="150px">
        <router-link to="./adminPersonalInformation">
          <div id="information">
          管理员姓名<br/>
          账号<br/>
          邮箱<br/>
          </div>
        </router-link>
      </el-aside>

      <el-main id="body">
        功能权限
        <el-row>
          <el-col :span="8" :offset="index > 0 ? 2 : 0">
            <el-card :body-style="{ padding: '0px' }">
              <img src="../../assets/用户账号管理.png" class="image">
              <div style="padding: 14px;">
                <span>用户账号管理</span>
                <div class="bottom clearfix">
                  <time class="time">{{ currentDate }}</time>
                  <el-button type="text" class="button" @click="hrefAdminUserAccount">点击跳转</el-button>
                </div>
              </div>
            </el-card>
          </el-col>

          <el-col :span="8" :offset="index > 0 ? 2 : 0">
            <el-card :body-style="{ padding: '0px' }">
              <img src="../../assets/发起活动类型.png" class="image">
              <div style="padding: 14px;">
                <span>发起活动类型</span>
                <div class="bottom clearfix">
                  <time class="time">{{ currentDate }}</time>
                  <el-button type="text" class="button" @click="hrefAdminActivityType">点击跳转</el-button>
                </div>
              </div>
            </el-card>
          </el-col>

          <el-col :span="8" :offset="index > 0 ? 2 : 0">
            <el-card :body-style="{ padding: '0px' }">
              <img src="../../assets/打分情况处理.png" class="image">
              <div style="padding: 14px;">
                <span>打分情况处理</span>
                <div class="bottom clearfix">
                  <time class="time">{{ currentDate }}</time>
                  <el-button type="text" class="button" @click="hrefAdminScoring">点击跳转</el-button>
                </div>
              </div>
            </el-card>
          </el-col>

          <el-col :span="8" :offset="index > 0 ? 2 : 0">
            <el-card :body-style="{ padding: '0px' }">
              <img src="../../assets/查看系统日志.png" class="image">
              <div style="padding: 14px;">
                <span>查看系统日志</span>
                <div class="bottom clearfix">
                  <time class="time">{{ currentDate }}</time>
                  <el-button type="text" class="button" @click="hrefAdminSystemLog">点击跳转</el-button>
                </div>
              </div>
            </el-card>
          </el-col>

           <el-col :span="8" :key="o" :offset="index > 0 ? 2 : 0">
            <el-card :body-style="{ padding: '0px' }">
              <img src="../../assets/发布公告公示.png" class="image">
              <div style="padding: 14px;">
                <span>发布公告公示</span>
                <div class="bottom clearfix">
                  <time class="time">{{ currentDate }}</time>
                  <el-button type="text" class="button" @click="hrefAdminBoardApply">点击跳转</el-button>
                </div>
              </div>
            </el-card>
          </el-col>
        </el-row>
      </el-main>

      <el-footer id="footer" height="150px">

      </el-footer>
    </el-container>
  </div>
</template>
<script>
export default {
  data() {
    return {
      currentDate: new Date()
    };
  },
  methods: {
    handleOpen(key, keyPath) {
      console.log(key, keyPath);
    },
    handleClose(key, keyPath) {
      console.log(key, keyPath);
    },

    hrefExit()
    {
      this.$router.push({path:'./'});
    },

    hrefAdminBoardApply()
    {
      this.$router.push({path:'./adminBoardApply'});
    },

    hrefAdminUserAccount()
    {
      this.$router.push({path:'./adminUserAccount'});
    },

    hrefAdminActivityType()
    {
      this.$router.push({path:'./adminActivityType'});
    },

    hrefAdminScoring()
    {
      this.$router.push({path:'./adminScoring'});
    },

    hrefAdminSystemLog()
    {
      this.$router.push({path:'./adminSystemLog'});
    },
  }
};
</script>

<style scoped>
.time {
  font-size: 13px;
  color: #999;
}

.bottom {
  margin-top: 13px;
  line-height: 12px;
}

.button {
  padding: 0;
  float: right;
}

.image {
  width: 100%;
  display: block;
}

.clearfix:before,
.clearfix:after {
    display: table;
    content: "";
}

.clearfix:after {
    clear: both
}

#information {
    text-align: center;
}

#exit {
  position: absolute;
  right: 5px;
  bottom: 0px;
}

#board {
  position: absolute;
  right: 0px;
  top: 0px;
  left: 0px;
  height: 400px;
  border: 1px solid #000000;
}

#hrefAdminBoardApply {
  position: absolute;
  right: 80px;
  top: 450px;  
}

#header {
  position: absolute;
  top: 0px;
  left: 0px;
  right: 0px;
  bottom: 0px;
}

#body {
  position: absolute;
  left: 150px;
  right: 300px;
  top: 100px;
  bottom: 150px; 
  background-color: #f2f2f2;
}

#aside-left {
  position: absolute;
  left: 0px;
  top: 100px;
  bottom: 150px;
  border: 1px solid;
  /*box-shadow: 0 2px 12px 0 rgba(0, 0, 0, 0.1);*/
}

#aside-right {
  position: absolute;
  right: 0px;
  top: 100px;
  bottom: 150px;
}

#footer {
  position: absolute;
  bottom: 0px;
  left: 0px;
  right: 0px;
}
</style>