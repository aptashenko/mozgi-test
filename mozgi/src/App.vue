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
  animation-name: normalText;
  animation-duration: 10s;
  animation-timing-function: linear;
  animation-iteration-count: infinite;
  animation-direction: alternate;

  pointer-events: none;
  @media (min-width: 768px) {
    left: 0;
    transform: rotateZ(306deg) translate(-500px, 0px);
  }
}

.reversedText {
  animation-name: reversedText;
  animation-duration: 10s;
  animation-timing-function: linear;
  animation-iteration-count: infinite;
  animation-direction: alternate;
  pointer-events: none;
  @media (min-width: 768px) {
      transform: rotateZ(126deg) translate(800px, 25px);
    }
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
    transform: rotateZ(306deg) translateX(-500px);
  }
  100% {
    transform: rotateZ(306deg) translateX(-550px);
  }
}
@keyframes reversedText {
  0% {
    transform: rotateZ(126deg) translate(800px, 25px);
  }
  100% {
    transform: rotateZ(126deg) translate(750px, 25px);
  }
}

</style>
