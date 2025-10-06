<script setup lang="ts">
import ChatWindow from '~/components/ChatWindow.vue'
import useChat from '~/composables/useChat'

const { chat, messages, sendMessage } = useChat()
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
