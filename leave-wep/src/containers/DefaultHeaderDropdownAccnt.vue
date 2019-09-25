<template>
  <AppHeaderDropdown right no-caret>
    <template slot="header">
      <span> {{ name }} </span>
     
    </template>
    <template slot="dropdown">
      <b-dropdown-item><a><i class="fa fa-user" /> Edit Password</a></b-dropdown-item>
      <b-dropdown-item><a v-on:click="logout()" ><i class="fa fa-lock" /> Logout</a></b-dropdown-item>
    </template>
  </AppHeaderDropdown>
</template>

<script>
import { HeaderDropdown as AppHeaderDropdown } from '@coreui/vue'
export default {
  name: 'DefaultHeaderDropdownAccnt',
  components: {
    AppHeaderDropdown
  },
  data: () => {
    return { itemsCount: 42,
              name: localStorage.username
    }
  },
   methods: {
      async logout() {
          localStorage.token = ""
          localStorage.firstname = ""
          localStorage.lastname = ""
          localStorage.role = ""
          localStorage.username = ""
          this.$router.push({ path: '/pages/login'})
      },
  },
}
</script>
