<script setup lang="ts">
import ChatWindow from '~/components/ChatWindow.vue'
import useChat from '~/composables/useChat'

const { chat, messages, sendMessage } = useChat()

const appConfig = useAppConfig()
const title = computed(() =>
  chat.value?.title
    ? `${chat.value.title} - ${appConfig.title}`
    : appConfig.title
)

useHead({
  title
})
</script>

<template>
  <div class="layout-container">
    <ChatWindow
      :chat
      :messages
      @send-message="sendMessage"
    />
  </div>
</template>

<style scoped>
  .layout-container {
    background-color: var(--background-color-primary);
  }
</style>
