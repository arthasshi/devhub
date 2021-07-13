<template>
  <div class="Upcoming">
    <div class="title">Comleted Bookings</div>
    <div class="item">
      <div class="title">
        <div class="name">Lighting Service</div>
        <div class="enter">Service description ></div>
      </div>
      <div class="middle">
        <div class="left">
          <div class="name-value">
            <div class="name">Contact Name</div>
            <div class="value">Tom</div>
          </div>
          <div class="name-value">
            <div class="name">Contact Num</div>
            <div class="value">12223212121</div>
          </div>
          <div class="name-value">
            <div class="name">Service Address</div>
            <div class="value">12 west st.c canley voie</div>
          </div>
          <div class="name-value">
            <div class="name">Service Time</div>
            <div class="value">12 west st.c canley voie</div>
          </div>
        </div>
        <div class="right">
          <div class="desc">Full Refund</div>
          <div class="name-money">
            <div class="name">Amount Paid</div>
            <div class="money">$50</div>
          </div>
          <div class="name-money">
            <div class="name">Amount Paid</div>
            <div class="money">$50</div>
          </div>
        </div>
      </div>
      <div class="divider"></div>
      <div class="tip">Booking Canceled</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      data: {} //如果有接口的话，可以通过接口请求数据渲染
    };
  }
};
</script>

<style lang="scss" scoped>
%col {
  display: flex;
  flex-direction: column;
  align-items: center;
}
%row {
  display: flex;
  flex-direction: row;
  align-items: center;
}
.Upcoming {
  width: 100%;
  height: 100%;
  @extend %col;
  justify-content: flex-start;
  align-items: flex-start;
  padding-left: 20px;
  .title {
    font-size: 16px;
    margin-bottom: 20px;
  }
  .item {
    -webkit-box-shadow: #f5f5f5 0px 0px 20px;
    -moz-box-shadow: #f5f5f5 0px 0px 20px;
    box-shadow: #f5f5f5 0px 0px 20px;
    width: 500px;
    height: auto;
    border-radius: 8px;
    padding: 20px;
    .title {
      @extend %row;
      justify-content: space-between;
      padding-bottom: 15px;
      margin-bottom: 15px;
      border-bottom: 2px solid #f5f5f5;
      .name {
        font-size: 15px;
        font-weight: bold;
        color: #000;
      }
      .enter {
        color: #ff935b;
      }
    }
    .middle {
      width: 100%;
      @extend %row;
      justify-content: space-between;
      .left {
        width: 60%;
        @extend %row;
        justify-content: flex-start;
        align-items: flex-start;
        flex-wrap: wrap;
        .name-value {
          @extend %col;
          justify-content: flex-start;
          align-items: flex-start;
          width: auto;
          margin-right: 40px;
          margin-bottom: 20px;
          text-align: start;
          .name {
            color: #666;
          }
        }
      }
      .right {
        height: 100%;
        width: 24%;
        border-left: 1px solid #cccaca;
        padding-left: 20px;
        .desc {
          color: #ff935b;
          width: 100%;
          text-align: start;
        }
        .name-money {
          @extend %col;
          justify-content: flex-start;
          align-items: flex-start;
          margin-bottom: 20px;
        }
      }
    }
    .divider {
      height: 4px;
      background: #ccc;
      width: 100%;
      margin-bottom: 2px;
    }
    .tip {
      width: 100%;
      font-size: 12px;
      text-align: end;
    }
  }
}
</style>
