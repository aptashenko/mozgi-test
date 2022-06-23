<template>
  <mainPage />
  <div class="normalText">
    <p class="backText">{{backgroundText}}</p>
    <p class="backText">{{ backgroundText }}</p>
  </div>
  <div class="reversedText">
    <p class="backText backText-reversed">{{ reversedText }}</p>
    <p class="backText backText-reversed">{{ reversedText }}</p>
  </div>
</template>

<script>
import mainPage from '@/components/mainPage';
import '@/assets/style/normalize.scss';
import '@/assets/style/font.css';

export default {
  name: 'App',
  components: {
    mainPage,
  },
  data() {
    return {
      backgroundText: 'FULL-CYCLE EVENT AGENCY',
    }
  },
  computed: {
    reversedText() {
      return this.backgroundText.split('').reverse().join('');
    },
  },
}
</script>

<style lang="scss">
html, #app {
  height: 100%;
  display: flex;
  flex-direction: column;
}
#app {
  overflow: hidden;
}
body {
  height: 100%;
  background: #BEBEBE;
  font-family: 'GrtskGiga';
  color: #373737;
}
h1, h2, h3, h4, ul, p, a {
  text-decoration: none;
  color: #363636;
  margin: 0;
  padding: 0;
}

.normalText, .reversedText {
  display: flex;
  position: fixed;
  white-space: nowrap;
  width: 200%;
}

.normalText {
  bottom: 0;
  left: -351px;
  animation: normalText 10s linear infinite;
  transform: rotateZ(300deg);
  pointer-events: none;
}

.reversedText {
  top: 0;
  right: -358px;
  animation: reversedText 10s linear infinite;
  transform: rotateZ(120deg);
  pointer-events: none;
}

.backText {
  display: inline;
  font-size: 28px;
  line-height: 1.1;
  text-align: center;
  text-transform: uppercase;
  color: #bebebe;
  opacity: 0.1;
  text-shadow: 0px 1px 0 rgb(55, 55, 55), 0px -1px 0 rgb(55, 55, 55), 1px 0px 0 rgb(55, 55, 55), -1px 0px 0 rgb(55, 55, 55), 1px 1px 0 rgb(55, 55, 55), 1px -1px 0 rgb(55, 55, 55), -1px 1px 0 rgb(55, 55, 55), -1px -1px 0 rgb(55, 55, 55);
}

@keyframes normalText {
  0% {
    transform: rotateZ(300deg) translateX(330px);
  }
  100% {
    transform: rotateZ(300deg) translateX(-150px);
  }
}
@keyframes reversedText {
  0% {
    transform: rotateZ(120deg) translateX(360px);
  }
  100% {
    transform: rotateZ(120deg) translateX(-170px);
  }
}

</style>
