<template>
  <el-breadcrumb class="breadcrumb" separator="/">
    <transition-group name="breadcrumb">
      <el-breadcrumb-item
        v-for="(item, index) in breadcrumbData"
        :key="item.path">
        <!--      可点击项-->
        <span class="no-redirect" v-if="index === breadcrumbData.length-1">
        {{ generateTitle(item.meta.title) }}
      </span>
        <!--      不可点击项-->
        <span class="redirect" @click="onLinkClick(item)" v-else>
        {{ generateTitle(item.meta.title) }}
      </span>
      </el-breadcrumb-item>
      </transition-group>
  </el-breadcrumb>
</template>

<script setup>
import { ref, watch } from 'vue'
import { useRoute, useRouter } from 'vue-router'
import { useStore } from 'vuex'
import { generateTitle } from '@/utils/i18n.js'

// 生成数组数据
const breadcrumbData = ref([])
const getBreadcrumbData = () => {
// 当前路由的标准化路由记录
  breadcrumbData.value = route.matched.filter(
    item => item.meta && item.meta.title
  )
}

// 监听路由变化
const route = useRoute()
watch(route, () => {
  getBreadcrumbData()
}, {
  immediate: true
})

// 跳转点击时间
const router = useRouter()
const onLinkClick = (item) => {
  router.push(item.path)
}
// 将来需要主题替换，所以将 hover 的颜色设为主题色
const store = useStore()
const linkHoverColor = ref(store.getters.cssVar.menuBg)
</script>

<style lang="scss" scoped>
.breadcrumb {
  display: inline-block;
  font-size: 14px;
  line-height: 50px;
  margin-left: 8px;

  .redirect {
    color: #666;
    font-weight: 600;
    cursor: pointer;
  }

  .redirect:hover {
    color: v-bind(linkHoverColor);
  }

  ::v-deep .no-redirect {
    color: #97a8be;
    cursor: text;
  }
}
</style>
