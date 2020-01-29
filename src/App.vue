<template>
  <v-app>
    <v-app>
      <Header v-if="!isScrollDown" />
      <router-view :key="$route.fullPath" />
      <!-- <Footer /> -->
    </v-app>
  </v-app>
</template>

<script>
import Header from './components/Header'

export default {
  name: 'App',
  components: {
    Header,
  },
  data: () => ({
    offsetY: 0,
    isScrollDown: false
  }),
  watch: {
        offsetY (newOffset, oldOffSet) {
            if(newOffset - oldOffSet > 0) {
              console.log('down')
              this.isScrollDown = true
            } else {
              console.log('up')
              this.isScrollDown = false
            }
        }
    },
    mounted () {
        this.$nextTick(() => {
            window.addEventListener('scroll', () => {
                this.offsetY = window.scrollY
            })
        })
    },
};
</script>
<style>
#app {
  font-family: 'Open Sans', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: #eeeff1!important;
}

p {
  font-size: 15px;
  text-align: left;
  font-weight: 400;
  margin-bottom: 8px;
  color: #576366;
  line-height: 21px;
  font-family: 'Open Sans';
}

h1, h2 {
  color: #374047;
}

@media only screen and (max-width: 1000px) {
  h1 {
    font-size: 20px;
  }
}

.normal-card {
    box-shadow: 0 2px 0 rgba(0,0,0,0.06)!important;
}
</style>
