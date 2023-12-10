<template>
    <div>
        <form class="chat-button">
            <input type="text" placeholder="Написать сообщение..." v-model="msg">
            <button v-if="msg.length" @click="sentMsg"><img src="../assets/img/btn__search.svg" alt=""></button>
            <button v-else @click.prevent="sentMsg, btn = !btn"><img src="../assets/img/btn__scrin.svg" alt=""></button>
        </form>
        <div class="panel" v-if="btn">
            <div class="panel-wrap">
                <div class="panel-wrap-title">Отправить картинку</div>
                <form class="panel-wrap-form">
                    <input class="panel-wrap-form-file" type="text" v-model="url" placeholder="URL">
                    <input class="panel-wrap-form-text" type="text" v-model="msgBtn" placeholder="Комментарий">
                    <div class="panel-wrap-btn">
                        <button class="panel-wrap-btn-sending" @click="sentMsg">ОТПРАВИТЬ</button>
                        <button class="panel-wrap-btn-back" @click="btn = !btn">Отмена</button>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            msg: '',
            msgBtn: '',
            url: '',
            btn: false,
        }
    },
    props: ['sender'],
    methods: {
        sentMsg() {
            let hour = new Date().getHours()
            let min = new Date().getMinutes()
            if (hour < 10) hour = '0' + hour
            else hour = hour
            if (min < 10) min = '0' + min
            else min = min
            const time = `${hour}:${min}`
            if (this.msg.length) {
                const message = {}
                message.body = this.msg.trim()
                message.sendId = this.sender
                message.time = time
                message.imageUrl = this.url,
                    this.$emit('msg', message)
            }
            else if (this.msgBtn.length) {
                const message = {}
                message.body = this.msgBtn.trim()
                message.sendId = this.sender
                message.time = time
                message.imageUrl = this.url,
                    this.$emit('msg', message)
            }
        },
    },
}


</script>

<style ></style>    