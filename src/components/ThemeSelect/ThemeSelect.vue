<template>
  <el-dropdown v-bind="$attrs"
               trigger="click"
               class="theme"
               @command="handleSetTheme"
  >
    <!--    图标-->
    <div>
      <el-tooltip :content="$t('msg.navBar.themeChange')">
        <div id="guide-theme">
          <svg-icon icon="change-theme" />
        </div>
      </el-tooltip>
    </div>
    <!--    menu-->
    <template #dropdown>
      <el-dropdown-menu>
        <el-dropdown-item command="color">
          {{ $t('msg.theme.themeColorChange') }}
        </el-dropdown-item>
      </el-dropdown-menu>
    </template>
  </el-dropdown>
  <!--  弹出层-->
  <div>
    <select-color v-model="selectColorVisible"></select-color>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import SelectColor from '@/components/ThemeSelect/components/SelectColor'

// dialog
const selectColorVisible = ref(false)

const handleSetTheme = command => {
  selectColorVisible.value = true
}
</script>

<style lang="scss" scoped></style>
