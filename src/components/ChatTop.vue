<template>
    <div>
        <div class="chat-top">
            <img :src="images[img]" alt="">
            <div class="chat-top-info">
                <h2>{{ name }}</h2>
                <span>Онлайн</span>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ['name', 'img'],
    data() {
        return {
            images: {
                alex: require('@/assets/img/alex.svg'),
                evgen: require('@/assets/img/evgen.svg')
            },

        }
    },
}
</script>

<style></style>