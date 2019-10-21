<template>
    <section>
        <header-bar :is-inner-fill="true"/>
        <div class="header-space"></div>
        <div class="message-frame">
            <h2>Coming soon...</h2>
        </div>
    </section>
</template>

<script>
import HeaderBar from '~/components/HeaderBar.vue'

export default {
    components: {
        HeaderBar
    }
}
</script>

<style scoped>
.message-frame {
    width: 100%;
    height: 94vh;
    background: rgb(140, 175, 185);
    color: white;
    font-family: 'Tahoma';
    text-align: center;
    padding-top:50%;
}
.message-frame>h2 {
    font-size: 10vw;
    transform: rotate(-10deg);
}
</style>