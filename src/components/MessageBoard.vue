<script setup>
defineProps({
  messages: {
    type: Array,
    required: true
  }
})

</script>

<template>
  <div class="message-board">
    <h2 class="message-board-title">Message Board</h2>
    <TransitionGroup tag="ul" name="slide" class="message-board-list">
      <li v-for="message in messages" :key="message.id">
        <slot :message="message"></slot>
      </li>
    </TransitionGroup>
  </div>
</template>

<style>
.slide-enter-active,
.slide-leave-active {
  transition: transform 0.5s;
}

.slide-enter-from {
  transform: translateY(-100%);
}
</style>
