<template>
  <div id="detail">
    <div class="member_list e_card">
      <div class="title">宿舍编号：{{roomId}} | 成员分布</div>
      <hr>
      <el-row :gutter="20" class="member_box">
        <el-col :span="8" class="member" v-for="item in memberList" :key="item.uid">
          <div class="inner">
            <div class="name">{{item.name}}</div>
            <div class="time">
              <div class="getUptime">起床时间：{{item.getUpTime}}</div>
              <div class="sleepTime">睡觉时间：{{item.sleepTime}}</div>
            </div>
          </div>
        </el-col>
      </el-row>
    </div>
    <div class="feedback_list">
      <div class="feedback e_card" v-for="item in feedBackList" :key="item.id">
        <div class="comment">
          {{item.name}}：{{item.comment}}
        </div>
        <el-rate
          v-model="item.harmonious"
          disabled
          show-score
          text-color="#ff9900"
          score-template="{value}.0 分"
        ></el-rate>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      roomId: this.$route.params.id,
      memberList: [],
      feedBackList: []
    };
  },
  methods: {
    getRoomInfo() {
      this.axios
        .get("/getRoomInfo?id=" + this.roomId)
        .then(res => {
          if (res.data.code == 1) {
            this.memberList = res.data.data.memberList;
            this.feedBackList = res.data.data.feedBackList;
          }
        })
        .catch(err => {
          console.log(err);
          this.$message.error("服务器无法连接");
        });
    }
  },
  mounted(){
    this.getRoomInfo();
  }
};
</script>

<style lang='scss' scoped>
.member_list {
  .title {
    font-size: 20px;
  }
  .member_box {
    display: flex;
    .member {
      .inner {
        background-color: #67c23a;
        color: #ffffff;
        padding: 20px;
        border-radius: 10px;
        .name {
          padding-bottom: 20px;
          margin-bottom: 20px;
          border-bottom: 1px solid #fff;
          font-size: 20px;
          font-weight: bold;
        }
        .time {
          display: flex;
          justify-content: space-between;
        }
      }
    }
  }
}
.feedback {
  margin: 30px 0;
  .comment{
    margin-bottom: 20px;
  }
}
</style>