<template>
  <header>
    <Logo />
    <div class="nav nav-pills">
      <div 
        v-for="nav in navigations" 
        :key="nav.name"
        class="nav-item">
        <RouterLink 
          :to="nav.href" 
          :class="{ active: isMatch(nav.path) }"
          active-class="active"
          class="nav-link">
          {{ nav.name }}
        </RouterLink>
      </div>
    </div>
    <div 
      class="user"
      @click="toAbout">
      <img 
        :src="image" 
        :alt="name"
         style="border-radius:50%;" >
    </div>
  </header>
</template>

<script>
import Logo from '~/components/Logo'
import { mapState } from 'vuex'

export default {
  components: {
    Logo
  },
  data() {
    return {
      navigations: [
        {
          name: 'SEARCH',
          href: '/'
        },
        {
          name: 'MOVIE',
          href: '/movie/tt15242330',
          path: /^\/movie/
        },
        {
          name: 'ABOUT',
          href: '/about'
        }
      ]
    }
  },
  methods: {
    isMatch(path) {
      if(!path) return false;
      return path.test(this.$route.fullPath);
    },
    toAbout() {
      this.$router.push('/about');
    }
  },
  computed: {
    ...mapState('about', [
      'image',
      'name'
    ])
  }
}
</script>

<style lang="scss" scoped>
@import "~/scss/main";

header { 
  height: 70px;
  padding: 0 40px;
  display: flex;
  align-items: center;
  position: relative;
  .logo {
    margin-right: 40px;
  }
  .user {
    width: 40px;
    height: 40px;
    padding: 6px;
    border-radius: 50%;
    box-sizing: border-box;
    background-color: $gray-200;
    cursor: pointer;
    position: absolute;
    top: 0;
    bottom: 0;
    right: 40px;
    margin: auto;
    transition: .4s;
    &:hover {
      background-color: darken($gray-200, 10%);
    }
    img {
      width: 100%;
    }
  }
  @include media-breakpoint-down(sm) {
    .nav {
      display: none;
    }
  }
}
</style>