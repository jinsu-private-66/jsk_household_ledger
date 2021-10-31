<template>
<div>
  <v-navigation-drawer permanent>
    <v-list>
      <v-list-item class="px-2">
        <h2><Strong>TokyoKane</Strong></h2>
      </v-list-item>

      <v-list-item link>
        <v-list-item-content>
          <v-list-item-title class="text-h6">
            Jinsu
          </v-list-item-title>
          <v-list-item-subtitle>jinsu6688@gmail.com</v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>
    </v-list>

    <v-divider></v-divider>

    <v-list
      nav
      dense
    >
      <v-list-item >
        <v-list-item-icon>
          <v-icon>mdi-folder</v-icon>
        </v-list-item-icon>
        <router-link to="/" class="navbar__link">HOME</router-link>
      </v-list-item>

      <v-list-item>
        <v-list-item-icon>
          <v-icon>mdi-star</v-icon>
        </v-list-item-icon>
          <router-link to="/withdrawal/new" class="navbar__link">지출기록</router-link>
      </v-list-item>

      <v-list-item link>
        <v-list-item-icon>
          <v-icon>mdi-account-multiple</v-icon>
        </v-list-item-icon>
        <router-link :to="currentYearMonthToCalendarUrl()" class="navbar__link">지출내역(캘린더)</router-link>
      </v-list-item>

      <v-list-item link>
        <v-list-item-icon>
          <v-icon>mdi-star</v-icon>
        </v-list-item-icon>
        <router-link to="/withdrawal?page=1" class="navbar__link">지출내역(전체)</router-link>
      </v-list-item>

      <v-list-item link>
        <v-list-item-icon>
          <v-icon>mdi-star</v-icon>
        </v-list-item-icon>
        <router-link :to="currentYearMonthToMonthUrl()" class="navbar__link">지출내역(월)</router-link>
      </v-list-item>
    </v-list>
  </v-navigation-drawer>
</div>
</template>

<script>
export default {
  methods: {
    currentYearMonthToMonthUrl () {
      const now = new Date();

      return `/withdrawal/month?year=${now.getFullYear()}&month=${now.getMonth() + 1}`;
    },
    currentYearMonthToCalendarUrl () {
      const now = new Date();

      return `/withdrawal/calendar?year=${now.getFullYear()}&month=${now.getMonth() + 1}`;
    },
  }
}
</script>

<style lang="scss" scoped>
.navbar {
  width: 100%;
  height: 50px;
  display: flex;
  &__links {
    width: 100%;
    display: flex;
    text-decoration: none;
    justify-content: space-between;
  }
  &__left-wrapper,
  &__right-wrapper {
    a {
      margin-left: 15px;
    }
  }
}
</style>
