<template>
  <div id="start">
    <div class="start-content">
      <header class="start-header">
        <img src="../assets/images/start/canju.png" alt /> 用餐人数
      </header>
      <p class="notice">请选择正确的用餐人数 ，小二马上给你送餐具</p>
      <div class="content">
        <ul class="user-list">
          <li>
            <span>1人</span>
          </li>
          <li>
            <span>2人</span>
          </li>
          <li>
            <span>3人</span>
          </li>
          <li>
            <span>4人</span>
          </li>
          <li>
            <span>5人</span>
          </li>
          <li>
            <span>6人</span>
          </li>
          <li>
            <span>7人</span>
          </li>
          <li>
            <span>8人</span>
          </li>
          <li>
            <span>9人</span>
          </li>
          <li>
            <span>10人</span>
          </li>
          <li>
            <span>11人</span>
          </li>
          <li>
            <span>12人</span>
          </li>
        </ul>
      </div>
    </div>
    <router-link to="/home">
      <div id="start" class="start">
        <span>开始点菜</span>
      </div>
    </router-link>
  </div>
</template>

<script>
export default {};
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
  .user-list {
    display: flex;
    // 溢出换行
    flex-wrap: wrap;
    padding: 0.5rem;
    li {
      width: 25%;
      box-sizing: border-box;
      padding: 0.5rem;
      span {
        display: block;
        width: 100%;
        height: 3.2rem;
        line-height: 3.2rem;
        text-align: center;
        background-color: #fff;
        border-radius: 0.5rem;
        border: 1px solid #ccc;
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