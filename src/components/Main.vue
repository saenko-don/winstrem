<template>
  <div style="padding-top: 100px" class="main">
    <b-card v-for="content in listsContent"
            :key="content"
            :id="content"
            :title="(content !== 'company' && content !== 'advantage') ? translateTitle(content) : null">
      <b-card-text>
        <b-card-title v-if="content === 'company'">Компания в цифрах</b-card-title>
        <b-card-title v-if="content === 'company'">Скрытые возможности работы с нами</b-card-title>
        <b-card-title v-if="content === 'advantage'">Скрытые возможности работы с нами</b-card-title>
        <b-card-title v-if="content === 'advantage'">Посекундная тарификация</b-card-title>
        <b-card-title v-if="content === 'advantage'">Наши кейси</b-card-title>
      </b-card-text>
    </b-card>
  </div>
</template>

<script>
export default {
  name: "Main",
  data: () => ({
    listsContent: ['fromMe', 'company', 'services', 'clients', 'advantage', 'contacts']
  }),
  methods: {
    translateTitle(page) {
      switch (page) {
        case 'company':
          return 'Компания';
        case 'services':
          return 'Услуги';
        case 'clients':
          return 'Наши клиенты';
        case 'advantage':
          return 'Преимущество работы с нами';
        case 'contacts':
          return 'Контакты';
        case 'fromMe':
          return 'О нас';
        default:
          return ''
      }
    },
  }
}
</script>

<style scoped>
.main {
  background-image: url("../assets/logo.webp");
}

</style>