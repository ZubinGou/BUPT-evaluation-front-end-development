<template>
  <div>
    <el-container direction="vertical">
      <el-header id="header" height="100px">
        <div id="exit">
          <el-button type="text" @click="herfExit">退出登陆</el-button>
        </div>
      </el-header>

      <el-aside id="aside-left" width="170px">
        <router-link to="./instructorPersonalInformation">
          <div id="information">
            <center>
            <h1>辅导员姓名</h1>
            <span v-show="is_get">{{ numberValidateForm.name }}</span><br>
            <h3>账号</h3>
            <span v-show="is_get">{{ numberValidateForm.userId }}</span><br>
            <h3>邮箱</h3>
            <span v-show="is_get">{{ numberValidateForm.email }}</span><br>
            </center>
          </div>
        </router-link>
      </el-aside>

      <el-main id="body">
        <h3 class="title-board">功能权限</h3>
        <el-row :gutter="20">
          <el-col :span="6">
            <div @click="hrefInstructorEvaluationExamination">
              <el-card :body-style="{ padding: '0px' }" class="option-card">
                <img src="../../assets/测评信息审核.png" class="image">
                <div>
                    <center>测评信息审核</center>
                </div>
              </el-card>
            </div>
          </el-col>

          <el-col :span="6">
            <div @click="hrefInstructorTransferDelegateAuthority">
              <el-card :body-style="{ padding: '0px' }" class="option-card">
                <img src="../../assets/转移下放权限.png" class="image">
                <div>
                    <center>转移下放权限</center>
                </div>
              </el-card>
            </div>
          </el-col>

          <el-col :span="6">
            <div @click="hrefInstructorBoardApply">
              <el-card :body-style="{ padding: '0px' }" class="option-card">
                <img src="../../assets/发布公告公示.png" class="image">
                <div>
                    <center>发布公告公示</center>
                </div>
              </el-card>
            </div>
          </el-col>

          <el-col :span="6">
            <div @click="hrefInstructorBoardExamination">
              <el-card :body-style="{ padding: '0px' }" class="option-card">
                <img src="../../assets/公告公示审核.png" class="image">
                <div>
                    <center>公告申请审核</center>
                </div>
              </el-card>
            </div>
          </el-col>
        </el-row>

        <h3 class="title-board">基本素质评价</h3>

        <el-row>
          <el-col :span="6">
            <div @click="hrefinstructorAssignCement">
              <el-card :body-style="{ padding: '0px' }" class="option-card">
                <img src="../../assets/指定打分.png" class="image">
                <div>
                    <center>指定给分</center>
                </div>
              </el-card>
            </div>
          </el-col>

          <el-col :span="6">
            <div @click="hrefInstructorClassCommitteeScoring">
              <el-card :body-style="{ padding: '0px' }" class="option-card">
                <img src="../../assets/班委评分.png" class="image">
                <div>
                    <center>班委评分</center>
                </div>
              </el-card>
            </div>
          </el-col>
        </el-row>
      </el-main>

      <el-aside id="aside-right" width="300px">
        <router-link to="./instructorBoard" id="board-router">
          <el-card id="board" shadow="never">
            <div v-html="item.title" v-for="item in board" :key=item id="board-title"></div>
          </el-card>
        </router-link>
        <!-- <el-button @click="hrefStudentBoardApply" id="hrefStudentBoardApply">申请公告公示</el-button> -->
        <p id="email">举报邮箱：123456789@asd.com</p>
      </el-aside>
      <el-footer id="footer" height="150px">

      </el-footer>
    </el-container>
  </div>
</template>
<script>
import request from "@/utils/request"; //打了大括号后显示找不到request函数
export default {
  data() {
    return {
      currentDate: new Date(),
      is_get: false,
      numberValidateForm: {
        name: null,
        classCharge: null,
        userId: null,
        email: null
      },
      board: []
    };
  },
  methods: {
    handleOpen(key, keyPath) {
      console.log(key, keyPath);
    },
    handleClose(key, keyPath) {
      console.log(key, keyPath);
    },

    herfExit()
    {
      this.$router.push({path:'./'});
    },

    hrefInstructorEvaluationExamination()
    {
      this.$router.push({path:'./instructorEvaluationExamination'});
    },

    hrefInstructorBoardApply()
    {
      this.$router.push({path:'./instructorBoardApply'});
    },

    hrefInstructorTransferDelegateAuthority()
    {
      this.$router.push({path:'./instructorTransferDelegateAuthority'});
    },

    hrefInstructorBoardExamination()
    {
      this.$router.push({path:'./instructorBoardExamination'});
    },

    hrefinstructorAssignCement()
    {
      this.$router.push({path:'./instructorAssignCement'});
    },

    hrefInstructorClassCommitteeScoring()
    {
      this.$router.push({path:'./instructorClassCommitteeScoring'});
    },
  },
  mounted: function() {
    var that = this;
    new Promise((resolve, reject) => {
      request({
        url: "/user/info/instructor",
        method: "get"
      })
        .then(response => {
          let data = JSON.parse(response.data);
          let state = data.success;
          if (state == true)
            console.log(data);
            that.numberValidateForm = data.personInfo;
            this.is_get = true;
        })
        .catch(error => {
          reject(error);
        });
    });

    //var that = this;
    new Promise((resolve, reject) => {
      request({
        url: "/notification?disqualify=false",
        method: "get"
      })
        .then(response => {
          let data = JSON.parse(response.data);
          let state = data.success;
          if (state == true)
            console.log(data);
            that.board = data.notification;
            this.is_get = true;
        })
        .catch(error => {
          reject(error);
        });
    });  
  }
};
</script>

<style scoped>
#board-title {
  color: gray;
}

.option-card {
  height: 300px;
  width: 230px;
}

.el-card:hover{
  margin-top: -1px;
  /* margin-left: -1px; */
  box-shadow: 2px 2px 6px rgba(0, 0, 0, .2);
  border-color: #eee;
  transition: all .2s ease-in-out;
  cursor: pointer;
}

.title-board {
  color: gray;
}

#email {
  position: absolute;
  right: 25px;
  top: 500px;
  color: gray;
}

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
  position: absolute;
  top: 40px;
  color: gray;
  left: 10%;
  right: 10%;
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
  text-decoration:none;
  border-radius: 0px;
  font-size: 18px;
}

#board-router {
  position: absolute;
  right: 0px;
  top: 0px;
  left: 0px;
  height: 400px;
  text-decoration:none;
}

#hrefStudentBoardApply {
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
  height: 94px;
  background: url("../../assets/北邮logo.png") no-repeat;
  box-shadow: 0 2px 4px rgba(0, 0, 0, .12), 0 0 6px rgba(0, 0, 0, .04);
}

#body {
  position: absolute;
  left: 170px;
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