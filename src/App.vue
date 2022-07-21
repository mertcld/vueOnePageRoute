<script>
import Home from './Home.vue'
import About from './About.vue'
import NotFound from './NotFound.vue'
import Company from './Comp.vue'
import Navbar from './Navbar.vue'
const routes = {
  '/': Home,
  '/about': About,
  '/company' : Company
}

export default {
  components:{
    Navbar
  },
  data() {
    return {
      currentPath: window.location.hash
    }
  },
  computed: {
    currentView() {
      return routes[this.currentPath.slice(1) || '/'] || NotFound
    }
  },
  mounted() {
    window.addEventListener('hashchange', () => {
		  this.currentPath = window.location.hash
		})
  }
}
</script>

<template>
  <navbar></navbar>
  <component :is="currentView" />
</template>