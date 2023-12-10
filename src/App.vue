<template>
  <section class="chat">
    <div class="chat-user">
      <ChatTop img="alex" name="Александр" />
      <ChatMain sender="1" :msgs="msgs" />
      <ChatButton sender="1" @msg="sendMsg" />
    </div>
    <div class="chat-user">
      <ChatTop img="evgen" name="Евгений" />
      <ChatMain sender="2" :msgs="msgs" />
      <ChatButton sender="2" @msg="sendMsg" />
    </div>
  </section>
</template>

<script>
import ChatTop from './components/ChatTop.vue';
import ChatMain from './components/ChatMain.vue';
import ChatButton from './components/ChatButton.vue';

export default {
  components: { ChatTop, ChatButton, ChatMain },
  data() {
    return {
      msgs: [],
    }
  },
  methods: {
    sendMsg(msg) {
      this.msgs.push(msg)
      localStorage.message = JSON.stringify(this.msgs)
    }
  },
  created() {
    const message = localStorage.message ? JSON.parse(localStorage.message) : []
    this.msgs = message
  },
}
</script>

<style></style>