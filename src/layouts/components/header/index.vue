<template>
  <div class="header-container">
    <div class="logo" @click="$router.push('/')">
      <svg-icon icon="logo" size="36" color="pink" />
      <span>music</span>
    </div>
    
    <div class="menu">
      <div class="guide">
        <el-button :icon="ArrowLeft" size="small" circle @click="$router.go(-1)" />
        <el-button :icon="ArrowRight" size="small" circle @click="$router.go(1)" />
      </div>
      <div class="search">
        <el-input
          v-model="searchContent"
          class="w-50 m-2"
          size="large"
          placeholder="搜索"
          :prefix-icon="Search"
        />
      </div>
      <div class="setting">
        <el-icon><Setting /></el-icon>
        <div class="user">
          <el-avatar :size="36" src="" />
          <span>user</span>
          <el-icon><CaretBottom /></el-icon>
        </div>
      </div>
    </div>

  </div>
</template>

<script setup lang="ts">
import {
  ArrowLeft,
  ArrowRight,
  Search,
  Setting,
  CaretBottom
} from '@element-plus/icons-vue'
import { ref } from 'vue'
import type { Ref } from 'vue'

let searchContent: Ref<string> = ref('')
</script>

<style lang="scss" scoped>
.header-container {
  @include basicFlexBox();
  width: 100%;
  height: 100%;
  .logo {
    width: 140px;
    height: 100%;
    font-size: 24px;
    line-height: 55px;
    color: $themeColor;
    cursor: pointer;
    .svg-icon {
      margin-right: 5px;
      vertical-align: -0.25em;
    }
  }
  .menu {
    @include basicFlexBox();
    width: calc(100% - 260px + 24px);
    height: 100%;
    .guide {
      :deep(.el-button):hover,
      :deep(.el-button):focus {
        background-color: #fff;
        border-color: #dcdfe6;
        .el-icon {
          color: #606266;
        }
      }
    }
    .search {
      width: 280px;
      :deep(.el-input) {
        .is-focus {
          box-shadow:  0 0 0 1px var(--el-input-hover-border-color) inset;
        }
        .el-input__wrapper {
          border-radius: 20px;
        }
      }
    }
    .setting {
      @include basicFlexBox();
      width: 160px;
      height: 100%;
      .user {
        @include basicFlexBox();
        cursor: pointer;
        .el-avatar {
          margin-right: 5px;
        }
      }
    }
  }
}
</style>