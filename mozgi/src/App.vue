<template>
    <mainPage />
</template>

<script>
import mainPage from '@/components/mainPage';
import '@/assets/style/normalize.scss';
import '@/assets/style/font.css';

export default {
  name: 'App',
  components: {
    mainPage,
  }
}
</script>

<style lang="scss">
html, #app {
  height: 100%;
}
body {
  height: 100%;
  background: #BEBEBE;
  font-family: 'GrtskGiga';
  color: #373737;
}
h1, h2, h3, h4, ul, p {
  margin: 0;
  padding: 0;
}

</style>
