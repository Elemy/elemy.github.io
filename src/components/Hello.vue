<template>
  <div class="hello">
    <div class="content">
      <dl>
        <dt><router-link to="/detail" class="content-title">回车、换行、和文件末尾空行</router-link></dt>
        <dd>回车和换行在不同系统下面定义不同，时不时会有一些小问题出来，git 经常出现的 No new line at the end of file 也让很多人费解，需要梳理一下</dd>
      </dl>
      <dl>
        <dt><router-link to="/detail" class="content-title">回车、换行、和文件末尾空行</router-link></dt>
        <dd>回车和换行在不同系统下面定义不同，时不时会有一些小问题出来，git 经常出现的 No new line at the end of file 也让很多人费解，需要梳理一下</dd>
      </dl>
      <dl>
        <dt><router-link to="/detail" class="content-title">回车、换行、和文件末尾空行</router-link></dt>
        <dd>回车和换行在不同系统下面定义不同，时不时会有一些小问题出来，git 经常出现的 No new line at the end of file 也让很多人费解，需要梳理一下</dd>
      </dl>
      <dl>
        <dt><router-link to="/detail" class="content-title">回车、换行、和文件末尾空行</router-link></dt>
        <dd>回车和换行在不同系统下面定义不同，时不时会有一些小问题出来，git 经常出现的 No new line at the end of file 也让很多人费解，需要梳理一下</dd>
      </dl>
    </div>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
.content{
  width: 40%;
  margin: 0 auto;
  padding: 60px 0;
  dl{
    margin-bottom: 70px;
    dt{
      margin-bottom: 15px;
      word-break: break-all;
      font-weight: bold;
      margin-bottom: 25px;
      padding-bottom: 10px;
      border-bottom: 2px solid #eee;
      text-align: left;
      .content-title{
        text-decoration: none;
        text-align: left;
        font-size: 24px;
        color: #444;
        &:hover{
          color:#42b983;
        }
      }
    }
    dd{
      color: #999;
      font-size: 14px;
      line-height: 1.6;
      text-align: left;
    }
  }
}
</style>
