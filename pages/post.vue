<template>
    <section>
        <header-bar :is-inner-fill="true" />
        <div class="wrapper">
            <div class="image-wrapper">
                <h2 class="form-title">画像を選択</h2>
                <input type="file" id="image-inputer" accept="image/*">
                <img id="image-view" src="~assets/camera-retro-solid.svg">
            </div>

        </div>
    </section>
</template>

<script>
import HeaderBar from '~/components/HeaderBar.vue'

export default {
    components: {
        HeaderBar
    },
    mounted() {
        this.$el.querySelector('#image-view')
        .addEventListener('click', () => {
            this.$el.querySelector('#image-inputer').click()
        }, false)
    },
}
</script>

<style scoped>
.wrapper {
    padding: 5vh 10vw;
    font-family: 'Tahoma';
    font-size: 5vw;
    color: white;
}

h2.form-title {

}

.image-wrapper {
    width: 80vw;
}

.image-wrapper>img {
    width: 100%;
    background: wheat;
}
</style>