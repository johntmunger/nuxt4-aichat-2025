<script setup lang="ts">
import ChatWindow from '~/components/ChatWindow.vue'
import useChat from '~/composables/useChat'

const typing = ref(false)

const handleSendMessage = async (message: string) => {
  typing.value = true
  await sendMessage(message)
  typing.value = false
}

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
      :typing
      :chat
      :messages
      @send-message="handleSendMessage"
    />
  </div>
</template>

<style scoped>
  .layout-container {
    background-color: var(--background-color-primary);
  }
</style>
