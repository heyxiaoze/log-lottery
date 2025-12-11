<script setup lang="ts">
import PlayMusic from '@/components/PlayMusic/index.vue'
import useStore from '@/store'
import { themeChange } from '@/utils'
import { storeToRefs } from 'pinia'
import { onMounted, ref } from 'vue'
import { useI18n } from 'vue-i18n'

const { t } = useI18n()
const globalConfig = useStore().globalConfig
const prizeConfig = useStore().prizeConfig
const system = useStore().system
const { getTheme: localTheme } = storeToRefs(globalConfig)
const { getPrizeConfig: prizeList } = storeToRefs(prizeConfig)

const tipDialog = ref()

// 设置当前奖列表
function setCurrentPrize() {
  if (prizeList.value.length <= 0) {
    return
  }
  for (let i = 0; i < prizeList.value.length; i++) {
    if (!prizeList.value[i].isUsed) {
      prizeConfig.setCurrentPrize(prizeList.value[i])

      break
    }
  }
}
</script>

<style scoped lang="scss"></style>
