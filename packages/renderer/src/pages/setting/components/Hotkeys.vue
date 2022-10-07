<script lang="ts" setup>
import { useI18n } from 'vue-i18n'

import AppTitle from '@/components/Title.vue'
import { useSettingStore } from '@/store/setting'
const { t } = useI18n()
const settingStore = useSettingStore()
</script>
<template>
  <div>
    <app-title path="common.hotkeys" />
    <div class="hotkeys-wrapper mt-2">
      <div class="hotkeys-header mb-2">
        <span>功能说明</span>
        <span>快捷键</span>
        <span>全局快捷键</span>
      </div>

      <div v-for="hotkey in settingStore.hotkeys" :key="hotkey.key" class="hotkeys-item mb-2">
        <span>{{ hotkey.name }}</span>
        <v-text-field density="compact" variant="outlined" hide-details :model-value="hotkey.hotkey"></v-text-field>
        <v-text-field
          density="compact"
          disabled
          variant="outlined"
          hide-details
          :model-value="hotkey.globalHotkey"
        ></v-text-field>
      </div>
    </div>
  </div>
</template>
<style scoped lang="scss">
.hotkeys-wrapper {
  max-width: 500px;
  .hotkeys-header {
    display: grid;
    grid-template-columns: 0.5fr repeat(2, 1fr);
    font-size: 0.75rem;
    gap: 12px;
  }
  .hotkeys-item {
    display: grid;
    grid-template-columns: 0.5fr repeat(2, 1fr);
    font-size: 0.75rem;
    gap: 12px;
    align-items: center;
  }
}
</style>
