<template>
  <div class="overflow-hidden rounded">
    <img class="w-full" :src="loveMalaysiaPhotoCardHead" alt="" />
    <img class="w-full" :src="loveMalaysiaPhotoCardTail" alt="" />
  </div>

  <div class="mb-4 px-8 py-8">
    <div class="text-xl">
      <span class="mr-2">말레이시아 선교팀</span>
      <span class="font-bold text-[#0D5597]">러브 말레이시아</span>
    </div>

    <div class="py-2">
      <p class="pb-1">
        <span class="mr-4 text-slate-700">장소</span>
        <span class="font-semibold">🇲🇾말레이시아 쿠칭</span>
      </p>

      <p>
        <span class="mr-4">기간</span>
        <span class="font-semibold">2024년 9월 14일(토) ~ 18일(수)</span>
      </p>
    </div>

    <div>
      <p class="mb-1">[마태복음 28장 18~20절]</p>
      <p ref="bibleVerseRef" class="break-keep" :class="getMinHeightByScreen(width)"></p>
    </div>
  </div>
</template>

<script setup lang="ts">
import Typewriter from 'typewriter-effect/dist/core'
import { onMounted, ref } from 'vue'
import { useWindowSize } from '@vueuse/core'
import loveMalaysiaPhotoCardHead from '@/assets/love-malaysia-photo-card-head.webp'
import loveMalaysiaPhotoCardTail from '@/assets/love-malaysia-photo-card-tail.webp'

const { width } = useWindowSize()

const bibleVerseRef = ref(null)
const bibleVerse =
  '<sup>18</sup> 예수께서 나아와 말씀하여 이르시되 하늘과 땅의 모든 권세를 내게 주셨으니 ' +
  '<sup>19</sup> 그러므로 너희는 가서 모든 민족을 제자로 삼아 아버지와 아들과 성령의 이름으로 세례를 베풀고 ' +
  '<sup>20</sup> 내가 너희에게 분부한 모든 것을 가르쳐 지키게 하라 볼지어다 내가 세상 끝날까지 너희와 항상 함께 있으리라 하시니라'

const getMinHeightByScreen = (width: number) => {
  if (width > 1124) {
    return 'h-[96px]'
  }
  if (width > 602) {
    return 'h-[120px]'
  }
  if (width > 425) {
    return 'h-[144px]'
  }
  if (width > 365) {
    return 'h-[168px]'
    // return 'h-[96px]'
  }
  // return 'h-[120px]'
  return 'h-[192px]'
}

onMounted(() => {
  const typewriter = new Typewriter(bibleVerseRef.value, {
    loop: false,
    delay: 40,
  })

  typewriter.pauseFor(500).typeString(bibleVerse).start()
})
</script>

<style scoped>
.pattern-bg-custom {
  --pattern-bg-color: #0d5597;
}
</style>
