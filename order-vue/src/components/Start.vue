<template>
  <div id="start">
    <div class="start-content">
      <header class="start-header">
        <img src="../assets/images/start/canju.png" alt /> 用餐人数
      </header>
      <p class="notice">请选择正确的用餐人数 ，小二马上给你送餐具</p>
      <div class="content">
        <ul class="user-list">
          <li v-for="(data,index) in personData" :key="index" :class="{'active':data.selected}">
            <span @click="selectPerson(index)">{{data.number}}人</span>
          </li>
        </ul>
        <!-- 备注信息 -->
        <div class="mark-input">
          <input type="text" placeholder="请输入您端口味要求、忌口等（可不填）" v-model="markInput" />
        </div>
        <ul class="mark-list">
          <li v-for="(data,index) in markData" :key="index" :class="{'active':data.selected}">
            <span @click="selectMark(index)">{{data.data}}</span>
          </li>
        </ul>
      </div>
    </div>
    <div id="start" class="start" @click="addPeopleInfo()">
      <span>开始点菜</span>
    </div>
  </div>
</template>

<script>
import config from '../model/config'
export default {
  data() {
    return {
      personData: [],
      currentSelected: 0,
      markInput: "",
      markData: [
        {
          selected: false,
          data: "打包带走"
        },
        {
          selected: false,
          data: "不要放辣椒"
        },
        {
          selected: false,
          data: "微辣"
        }
      ],
      api:config.api
    };
  },
  mounted() {
    this.initData();
  },
  methods: {
    initData() {
      let personData = [];
      for (let i = 0; i < 12; i++) {
        personData.push({ selected: false, number: i + 1 });
      }
      personData[0].selected = true;
      this.currentSelected = 0;
      this.personData = personData;
    },
    selectPerson(index) {
      this.personData[this.currentSelected].selected = false;
      this.personData[index].selected = true;
      this.currentSelected = index;
    },
    selectMark(index) {
      if (this.markData[index].selected) {
        this.markInput = this.markInput.replace(
          " " + this.markData[index].data,
          ""
        );
      } else {
        this.markInput = this.markInput + " " + this.markData[index].data;
      }
      this.markData[index].selected = !this.markData[index].selected;
    },
    addPeopleInfo() {
      let api=this.api+"api/addPeopleInfo"
      this.$http.post(api,{
        uid:"s001",
        p_num:this.currentSelected+1,
        p_mark:this.markInput
      }).then((res)=>{
        console.log(res)
        if(res.body.success=="true"){
          this.$router.push({
            path:"/home"
          })
        }
      },(error)=>{
        console.log(error)
      })
    }
  }
};
</script>

<style lang="scss">
.start-content {
  .start-header {
    height: 3.2rem;
    line-height: 3.2rem;
    background: #000;
    color: #fff;
    width: 10rem;
    margin: 5rem auto 0;
    border-radius: 0.5rem;
    img {
      height: 2.2rem;
      line-height: 2.2rem;
      position: relative;
      top: 0.5rem;
      margin-left: 1rem;
      margin-right: 0.4rem;
    }
  }

  .notice {
    color: red;
    text-align: center;
    margin: 1rem 0;
  }
  .mark-input {
    padding: 2rem;
    input {
      height: 4rem;
      line-height: 4rem;
      width: 100%;
      border: 1px solid #eee;
    }
  }
  .user-list,
  .mark-list {
    display: flex;
    // 溢出换行
    flex-wrap: wrap;
    padding: 0.5rem;
    li {
      width: 25%;
      box-sizing: border-box;
      padding: 0.8rem;
      span {
        display: block;
        width: 100%;
        height: 4.4rem;
        line-height: 4.3rem;
        text-align: center;
        background-color: #fff;
        border-radius: 0.8rem;
        border: 1px solid #ccc;
      }
    }
    .active {
      span {
        background-color: red;
        border: 1px solid #fff;
        color: #fff;
      }
    }
  }
}

.start {
  position: fixed;
  bottom: 5rem;
  left: 50%;
  width: 7.2rem;
  height: 7.2rem;
  background-color: red;
  color: #fff;
  border-radius: 50%;
  margin-left: -3.6rem;
  span {
    display: block;
    width: 3rem;
    margin: 0 auto;
    position: relative;
    top: 1.8rem;
  }
}
</style>