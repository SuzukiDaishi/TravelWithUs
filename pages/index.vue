<template>
  <section class="entire">
    <header-bar />
    <div class="imageview imageview-inside">
      <div>
        <h1 class="imageview-inside-logo">Have a smart tourism</h1>
      </div>
    </div>
    <div class="spots">
      <div class="spots-title">
        <h2>Feature Spot</h2>
      </div>
      <div class="spots-controller-wrapper">
        <button class="spots-controller" @click="backTransition">
          <img src="~assets/caret-left-solid.svg">
        </button>
        <button class="spots-controller" @click="nextTransition">
          <img src="~assets/caret-right-solid.svg">
        </button>
      </div>
      <div class="spots-list" :style="`width: ${50*spots.length}vw`">
        <div class="spot-box" v-for="(spot, index) in spots" :key="index" :id="`spot-${index}`">
          <div>
            <img :src="spot.image">
          </div>
          <span>{{spot.name}}</span>
        </div>
      </div>
    </div>
    <div>
      <div class="spotinfo">
        <div class="spotinfo-space"></div>
        <div class="spotinfo-title">
          <h2>Recommend Spot</h2>
          <hr>
        </div>
        <div class="spotinfo-map-box">
          <div v-html="spots[4].map">
          </div>
        </div>
        <div class="footer">
          <p>{{spots[4].description}}</p>
          <div class="spotinfo-button-wrapper">
          <button class="spotinfo-button spotinfo-button-left">
            <img src="~assets/caret-left-solid.svg">
          </button>
          <button class="spotinfo-button spotinfo-button-right">
            <img src="~assets/caret-right-solid.svg">
          </button>
        </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import anime from 'animejs/lib/anime.min.js';
import HeaderBar from '~/components/HeaderBar.vue'

export default {
  data() {
    return {
      spots: [
        {
          image: require('@/assets/higashi_chaya.jpg'),
          name: 'Higashi Chaya District',
          map: '',
          description: ''
        },
        {
          image: require('@/assets/kanazawa_castle.jpg'),
          name: 'Kanazawa Castle Park',
          map: '',
          description: ''
        },
        {
          image: require('@/assets/kenrokuen.jpg'),
          name: 'Kenrokuen Garden',
          map: '',
          description: ''
        },
        {
          image: require('@/assets/eki.png'),
          name: 'Kanazawa Station',
          map: '',
          description: ''
        },
        {
          image: require('@/assets/kanazawa21.jpg'),
          name: '21st Century Museum of Contemporary Art, kanazawa',
          map: `<iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3204.71936568206!2d136.65596131468422!3d36.56087897999855!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x5ff83380db53b801%3A0x512a01db8b6568c1!2s21st%20Century%20Museum%20of%20Contemporary%20Art%2C%20Kanazawa!5e0!3m2!1sen!2sjp!4v1570675797408!5m2!1sen!2sjp" width="100%" height="100%" frameborder="0" style=" border:0;" allowfullscreen=""></iframe>`,
          description: 'The 21st Century Museum of Contemporary Art Kanazawa (Kanazawa 12) is a musium of contemporary art Hirosaka, Kanazawa City, Ishikawa Prefecture.'
        }
      ],
      relativePosition: 0,
      spotListWidth: 0
    }
  },
  components: {
    HeaderBar
  },
  methods: {
    nextTransition() {
      if (this.relativePosition > -this.spots.length+2) this.relativePosition -= 1
      anime({
        targets: '.spot-box',
        translateX: this.$el.querySelector('#spot-0').clientWidth * this.relativePosition
      })
    },
    backTransition() {
      if (this.relativePosition < 0) this.relativePosition += 1
      anime({
        targets: '.spot-box',
        translateX: this.$el.querySelector('#spot-0').clientWidth * this.relativePosition
      })
    }
  }
}
</script>

<style scoped>
.entire {
  background: rgb(140, 175, 185);
  max-width: 100vw;
  min-height: 100vh;
  overflow-x: hidden;
}

/** image view begin */
.imageview {
  width: 100vw;
  max-width: 100vw;
  height: 60vh;
  display: inline-block;
  background-attachment: fixed;
  background-size: auto 60vh;
  background-position: left top;
  background-image: url("~assets/eki.png");
  background-repeat: no-repeat;
}

.imageview-inside {
  position: relative;
}

.imageview-inside>div {
  position: absolute;
  top: 50%;
  left: 50%;
  transform : translate(-50%,-50%);
  text-align: center;
  z-index: 50;
}

.imageview-inside-logo {
  width: 100%;
  height: 100%;
  white-space: nowrap;
  color: white;
  font-size: 10vw;
  font-weight: bold; 
  transform: rotate(-10deg);
  font-family: 'Monotype Corsiva', fantasy;
}

/** image view end */

/** future spot begin */

.spots {
  width: 100vw;
  height: 40vh;
  max-height: 40vh;
}

.spots-title {
  display: flex;
  height: 6vh;
  align-items: center;
  margin-left: 5vw;
}

.spots-title>h2 {
  font-size: 8vw;
  font-family: 'Tahoma';
  font-weight: bolder;
  color: white;
}

.spots-controller-wrapper {
  text-align: right;
  padding-right: 5vw;
}

.spots-controller {
  background-color: transparent;
  border: none;
  cursor: pointer;
  outline: none;
  padding: 0;
  appearance: none;
  width: 15vw;
  height: 7.5vh;
}

.spots-controller>img {
  width: 100%;
  height: 100%;
}

.spots-list {
  height: 40vw;
  padding-left: 2vw;
}

.spot-box {
  width: 40vw;
  height: 40vw;
  max-height: 25vh;
  background: rgb(28, 34, 38);
  margin-right: 1vw;
  display: inline-block;
  color: white;
  text-align: center;
}

.spot-box>div {
  height: 80%;
  width: 100%;
}

.spot-box>div>img {
  width: 100%;
  height: 100%;
}

.spot-box>span {
  width: 100%;
  display: inline-block;
  font-size: 1vh;
  text-align: center;
  vertical-align: middle;
  line-height:normal;
}

/** future spot end */

/** future spot begin */

.spotinfo {
  width: 100vw;
  height: 100vh;
}

.spotinfo-space {
  height: 6vh;
}

.spotinfo-title {
  width: 100vw;
  height: 12vh;
  font-size: 10vw;
  text-align: center;
  color: white;
  font-family: 'Tahoma';
}

.spotinfo-title>hr {
  background-color: white;
  text-align: center;
  width: 80%;
  height: 0.5vh;
  margin-top: 1.5vh;
  margin-bottom: 0;
  padding-top: 0;
  padding-bottom: 0;
}

.spotinfo-map-box {
  background: rgb(239, 50, 47);
  width: 100vw;
  height: 58vh;
  position: relative;
  display: table-cell;
  text-align: center;
  vertical-align: middle;
}

.spotinfo-map-box>div {
  width: 90%;
  height: 90%;
  display: inline-block;
}

.spotinfo-button-wrapper {
  vertical-align: text-bottom;
}

.footer {
  width: 100vw;
  height: 24vh;
  position: relative;
}

.footer>p {
  padding: 1vh 5vw;
  color: white;
  font-size: 5vw;
}

.spotinfo-button {
  background-color: transparent;
  border: none;
  cursor: pointer;
  outline: none;
  padding: 0;
  appearance: none;
  height: 7vh;
  width: 10vw;
  position: absolute ;
  bottom: 0;
}

.spotinfo-button-left {
  left: 5vw;
}

.spotinfo-button-right {
  right: 5vw;
}

.spotinfo-button>img {
  width: 100%;
  height: 100%;
}


/** future spot begin */

</style>

