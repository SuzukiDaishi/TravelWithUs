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
                <textarea rows="5" v-model="textData"></textarea>
            </div>
            <div class="place-wrapper">
                <h2 class="form-title">Set Place</h2>
                <select required v-model="placeData">
                    <option value="" hidden>Choose</option>
                    <option :value="spot.id" v-for="spot in spotsList" :key="spot.id">{{spot.name}}</option>
                </select>
            </div>
            <div class="submit-wrapper">
                <button>Submit</button>
            </div>
        </div>
    </section>
</template>

<script>
import HeaderBar from '~/components/HeaderBar.vue'
import axios from 'axios'

export default {
    components: {
        HeaderBar,
    },
    data() {
        return {
            imageData: require('@/assets/camera-retro-solid.svg'),
            isImageSelected: false,
            textData: "",
            placeData: "",
        }
    },
    async asyncData ({ params }) {
        let { data } = await axios.get(`http://travelwithus.sodeproject.com/api/spot/list`)
        return {
            spotsList: data
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
    font-family: 'Tahoma';
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
    height: calc( 5vh * 5 );;
    font-size: 5vh;
    border-radius: 5px;
    resize: none;
    overflow: hidden;
    border: 1px solid #000;
}

.place-wrapper {
    margin-top: 5vh;
}

.place-wrapper>select {
    width: 100%;
    height: 10vh;
    background: white;
    font-size: 5vh;
    border: 1px;
    background-image: url("~assets/angle-down-solid.svg");
    background-repeat: no-repeat;
    background-size: 10vw 10vh;
    background-position: right 2vw center;
}

.submit-wrapper {
    margin-top: 5vh;
}

.submit-wrapper>button {
    width: 100%;
    height: 10vh;
    border: 1px;
    font-size: 5vh;
    border-radius: 5px;
    background: #ddd;
}
</style>