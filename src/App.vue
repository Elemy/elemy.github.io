<template>
  <div id="app">
    <el-row type="flex" justify="space-around">
      <el-col :span="4" class="animatoggle" :class="{ toggleshow:isShowNav }">
        <div class="left-nav grid-content bg-purple">
          <el-input
            placeholder="请输入关键词"
            icon="search"
            v-model="keywordsinput"
            :on-icon-click="handleIconClick">
          </el-input>
          <el-menu default-active="2" class="el-menu-vertical-demo">
            <el-menu-item index="2">导航1</el-menu-item>
            <el-menu-item index="3">导航2</el-menu-item>
          </el-menu>
        </div>
      </el-col>
      <el-col :span="20">
        <div class="grid-content">
          <div class="toggle-icon" :class="{ moveright: isShowNav}">
            <input type="checkbox" id="toggle-menu" @change="toggleNav" :data-ischecked="isShowNav"/>
            <label for="toggle-menu">
              <span class="menu-icon"></span>
            </label>
          </div>
          <router-view></router-view>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      keywordsinput: '',
      isShowNav: false
    }
  },
  methods: {
    handleIconClick (ev) {
      console.log(ev)
    },
    toggleNav (e) {
      this.isShowNav = !(e.target.dataset.ischecked)
    }
  }
}
</script>

<style lang="less">
#app {
  font-family: 'PingFang SC', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.el-row {
  margin-bottom: 20px;
  &:last-child {
    margin-bottom: 0;
  }
}
.el-col {
  border-radius: 4px;
}
.animatoggle{
  position: absolute;
  left: -8.333333%;
  opacity: 0;
  transition: all .5s;
}
.toggleshow{
  left: 0;
  opacity: 1;
}
.left-nav {
  padding: 30px;
  background: #d3dce6;
  .el-input{
    margin-bottom: 20px;
  }
  .el-input__inner {
    border-color: #d3dce6;
  }
}
.grid-content{
  min-height: 400px;
}
.el-menu-item{
  background: #d3dce6;
  &.is-active{
    color: #48576a;
  }
  &:hover{
    color: #20a0ff;
  }
}

.toggle-icon{
  position: fixed;
  top: 10px;
  left: 8.3333%;
  z-index: 1;
  padding: 10px;
  transition: all .5s;
  &.moveright{
    left: 16.66666%;
  }
}
.menu-icon {
  font-size: 3em;
  max-width: 45px;
  text-align: center;
  display: block;
  margin: 15% auto;
  cursor: pointer;
  transition: transform .2s ease;
}
.menu-icon:hover {
  transform: scale(0.9);
}
.menu-icon:before, .menu-icon:after {
  line-height: .5;
}
.menu-icon:before {
  content: '☰';
  display: block;
}
.menu-icon:after {
  content: '╳';
  font-size: .75em;
  font-weight: 800;
  display: none;
}
#toggle-menu{
  display: none;
}
#toggle-menu:checked ~ label[for="toggle-menu"] .menu-icon {
  transform: rotate(180deg);
}
#toggle-menu:checked ~ label[for="toggle-menu"] .menu-icon:before {
  display: none;
}
#toggle-menu:checked ~ label[for="toggle-menu"] .menu-icon:after {
  display: block;
}
</style>
