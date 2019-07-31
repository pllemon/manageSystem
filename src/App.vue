<template>
  <div class="container flex-column" id="app">
    <Header></Header>
    <div class="flex flex1" style="width:100%">
      <Aside></Aside>
      <div class="flex-column flex1" style="overflow: hidden">
        <Tabs style="width: 100%;"></Tabs>
        <div class="main flex1">
          <keep-alive :include="tabsList">
              <router-view></router-view>
          </keep-alive>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Header from '@/components/Header.vue'
import Aside from '@/components/Aside.vue'
import Tabs from '@/components/Tabs.vue'

export default {
  data () {
    return {
      tabsList: []
    }
  },
  components: {
    Header,
    Aside,
    Tabs
  }
}
</script>

<style scoped lang="scss">
.container{
  width: 100%;
  height: 100%;
}
.el-aside{
  background: #fff;
}
.main{
  width: 100%;
}
</style>
