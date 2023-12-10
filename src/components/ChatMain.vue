<template>
    <div>
        <div class="chat-main">
            <transition-group name="list">
                <div class="chat-main-item" v-for="(msg, idx) in  msgs " :key="idx">
                    <div class="chat-main-item-content" :class="{
                        send: msg.sendId == sender,
                        get: msg.sendId != sender,
                    }
                        ">
                        <span>{{ msg.time }}</span>
                        <div class="chat-main-item-content-text">
                            <img v-if="msg.imageUrl" :src="msg.imageUrl" alt="">
                            <p>{{ msg.body }}</p>
                        </div>
                    </div>
                </div>
            </transition-group>
        </div>
    </div>
</template>

<script>
export default {
    props: ['msgs', 'sender', 'msgBtn'],
    data() {
        return {
        }
    },
}
</script>

<style></style>