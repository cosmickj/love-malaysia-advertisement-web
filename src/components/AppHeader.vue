<template>
  <header class="fixed top-0 z-10 flex w-full justify-end px-2 py-4 lg:py-2">
    <button class="btn btn-ghost btn-lg" onclick="my_modal_2.showModal()">
      <span class="underline underline-offset-2">후원 계좌 안내</span>
      <svg
        xmlns="http://www.w3.org/2000/svg"
        class="h-6 w-6"
        fill="none"
        viewBox="0 0 24 24"
        stroke="currentColor"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          stroke-width="2"
          d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z"
        />
      </svg>
    </button>

    <dialog id="my_modal_2" class="modal modal-bottom">
      <div class="modal-box">
        <form method="dialog">
          <button class="btn btn-circle btn-ghost absolute right-2 top-2">✕</button>
        </form>

        <h2 class="text-2xl font-bold">후원 계좌 안내</h2>

        <p class="py-2 text-lg">{{ source }} 이윤지</p>

        <div class="pt-2 text-end">
          <button v-if="isSupported" class="btn btn-primary btn-sm" @click="copy(source)">
            복사하기
          </button>
        </div>
      </div>

      <form method="dialog" class="modal-backdrop">
        <button>close</button>
      </form>

      <Transition>
        <div v-if="copied" class="toast toast-center toast-top w-full">
          <div class="alert">
            <span class="text-lg">응원해주셔서 감사합니다🙏</span>
          </div>
        </div>
      </Transition>
    </dialog>
  </header>
  <div class="p-4">
    <img class="w-24" :src="loveMalaysiaLogo" alt="love-malaysia-logo" />
  </div>
</template>

<script setup lang="ts">
import loveMalaysiaLogo from '@/assets/love-malaysia-logo.png'

import { useClipboard } from '@vueuse/core'

const source = '카카오 3333237544512'
const { copy, copied, isSupported } = useClipboard({ source })
</script>

<style scoped></style>
