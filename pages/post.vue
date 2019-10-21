<template>
    <section>
        <header-bar :is-inner-fill="true" />
        <div class="wrapper">
            <div class="image-wrapper">
                <h2 class="form-title">Update File</h2>
                <input type="file" id="image-inputer" accept="image/*" @change="changeImage">
                <img id="image-view" :src="imageData">
            </div>
            <div class="text-wrapper">
                <h2 class="form-title">Add Text</h2>
                <textarea rows="5"></textarea>
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
    data() {
        return {
            imageData: require('@/assets/camera-retro-solid.svg'),
            isImageSelected: false
        }
    },
    mounted() {
        this.$el.querySelector('#image-view')
        .addEventListener('click', () => {
            this.$el.querySelector('#image-inputer').click()
        }, false)
    },
    methods: {
        changeImage(event) {
            let image = event.target.files[0]
            let reader = new FileReader()
            reader.addEventListener("load", () => {
                this.imageData = reader.result
                this.isImageSelected = true
            }, false)
            if (image) {
                reader.readAsDataURL(image)
            }
        }
    }
}
</script>

<style scoped>
.wrapper {
    padding: 5vh 10vw;
}

h2.form-title {
    margin-bottom: 2vh;
    font-size: 8vw;
    font-family: 'Tahoma';
    color: white;
}

.image-wrapper {
    width: 80vw;
}

.image-wrapper>img {
    width: 100%;
    background: wheat;
}

#image-inputer {
    display: none;
}

.text-wrapper {
    margin-top: 5vh;
}

.text-wrapper>textarea {
    width: 100%;
    height: calc( 1.5em * 5 );;
    font-size: 1.5em;
    border-radius: 5px;
    resize: none;
    overflow: hidden;
    border: 1px solid #000;
}
</style>