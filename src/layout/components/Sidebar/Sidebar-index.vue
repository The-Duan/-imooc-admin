<template>
  <div class="">
    <div class="logo-container">
      <el-avatar
        :size="44"
        shape="square"
        src="https://mms1.baidu.com/it/u=4113123888,3436296091&fm=253&app=120&f=JPEG&fmt=auto&q=75?w=500&h=500">

      </el-avatar>
      <h1 class="logo-title" v-if="$store.getters.sidebarOpened">
        imooc-admin
      </h1>
    </div>
    <el-scrollbar>
      <SidebarMenu/>
    </el-scrollbar>
  </div>
</template>

<script setup>
import SidebarMenu from '@/layout/components/Sidebar/SidebarMenu'

</script>

<style lang="scss" scoped>
.logo-container {
  height: 44px;
  padding: 10px 0 22px 0;
  display: flex;
  align-items: center;
  justify-content: center;

  .logo-title {
    margin-left: 10px;
    color: #fff;
    font-weight: 600;
    line-height: 50px;
    font-size: 16px;
    white-space: nowrap;
  }
}
</style>
