<template>
    <headerPage />
    <heroPage />
</template>

<script>
import headerPage from '@/components/headerPage';
import heroPage from '@/components/heroPage';
import '@/assets/style/normalize.scss';
import '@/assets/style/font.css';

export default {
  name: 'App',
  components: {
    headerPage,
    heroPage,
  },
  data() {
    return {
    }
  },
  computed: {
  },
}
</script>

<style lang="scss">
html {
  height: 100%;
}
body {
  background: #BEBEBE;
  font-family: 'GrtskGiga';
  color: #363636;
  height: 100%;
}
#app {
  display: flex;
  flex-direction: column;
  height: 100%;
}
</style>
