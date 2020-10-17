<template>
  <div class="nav-wrap"
       id="main"
       :style="{...(!isActiveLogo ? {margin: '-40px'} : null)}"
       :class="{fixedNav: isActiveNav}">
    <img src="../assets/logo.webp"
         v-if="isActiveLogo"
         class="logo"
         alt="winstrim">
    <b-nav justified
           :style="{width: '100%'}">
      <b-nav-item v-for="link in links"
                  @click="test(link)"
                  :href="`#${link}`"
                  :key="link">{{ translateTitlePage(link) }}
      </b-nav-item>
    </b-nav>
  </div>
</template>

<script>
export default {
  name: "Header",

  data: () => ({
    activePage: 'main',
    links: ['main', 'clients', 'contacts', 'fromMe'],
    isActiveNav: false,
    isActiveLogo: true,
    scroll: 0,
  }),

  mounted() {
    window.addEventListener('scroll', this.handleScroll)
  },

  methods: {
    handleScroll() {
      this.isActiveLogo = window.scrollY < 100;
      this.isActiveNav = window.scrollY > 100 && window.scrollY < this.scroll;
      this.scroll = window.scrollY;
    },

    translateTitlePage(page) {
      switch (page) {
        case 'main':
          return 'Главная';
        case 'clients':
          return 'Клиенты';
        case 'contacts':
          return 'Контакты';
        case 'fromMe':
          return 'О нас';
        default:
          return ''
      }
    },

    test(page) {
      this.activePage = page;
    }
  },
}
</script>

<style scoped>

.nav-wrap {
  display: flex;
  background-color: aliceblue;
  top: 0;
  position: absolute;
  width: 100%;
  z-index: 1;
  padding: 0 40px;
  transition: 0.5s;
}

.fixedNav {
  position: fixed;
  transform: translate(0,40px);
}

.logo {
  height: 100px;
  width: 56px;
}
</style>