<template>
  <div class="home">
    <!-- 这个导航栏也可以独立出来变成导航组件 -->
    <div class="nav">
      <div
        class="item"
        :class="{ 'sel-item': currentName == i.name }"
        v-for="i in navMenus"
        :key="i.name"
        @click="go2Page(i)"
      >
        {{ i.name }}
        <div class="child" v-if="i.children && currentName == i.name">
          <div
            class="child-item"
            :class="{ 'sel-child-item': $route.name == j.name }"
            v-for="j in i.children"
            @click.stop="go2Page(j)"
            :key="j.name"
          >
            {{ j.name }}
          </div>
        </div>
      </div>
    </div>
    <div class="main">
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "home",
  components: {},
  data() {
    return {
      currentName: "",
      /* 这个导航列表也可以使用router */
      navMenus: [
        {
          name: "My Profile",
          path: "mp"
        },
        {
          name: "Address Book",
          path: "ab"
        },
        {
          name: "Booking History",
          path: "/Bk/Upcoming",
          children: [
            {
              name: "Upcoming",
              path: "/Bk/Upcoming"
            }
          ]
        },
        {
          name: "Payments Details",
          path: "pd"
        },
        {
          name: "Update Password",
          path: "up"
        },
        {
          name: "Log out",
          path: "/Logout"
        }
      ]
    };
  },
  mounted() {},
  methods: {
    go2Page(i) {
      /* 判断一下，防止重复跳转报错 */
      if (this.currentName == i.name) {
        return;
      }
      if (this.$route.path == i.path) {
        return;
      }
      this.$router.push(i.path);
      this.currentName = i.name;
    }
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
.home {
  @extend %row;
  justify-content: flex-start;
  .nav {
    @extend %col;
    justify-content: flex-start;
    align-items: flex-start;
    padding: 20px;
    width: 20%;
    height: 100vh;
    max-width: 200px;
    min-width: 120px;
    .sel-item {
      color: #ff935b;
    }
    .item {
      margin-bottom: 20px;
      cursor: pointer;
      .child {
        width: 100%;
        height: auto;
        margin: 20px 0 0 10px;

        padding-left: 10px;
        border-left: 4px #ff935b solid;
        @extend %col;
        justify-content: flex-start;
        align-items: flex-start;
        .child-item {
          margin-bottom: 5px;
          cursor: pointer;
        }
        .sel-child-item {
          color: #ff935b;
        }
      }
    }
  }
  .main {
    flex: 1;
    width: 80%;
    height: 100vh;
  }
}
</style>
