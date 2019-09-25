<template>
  <AppHeaderDropdown right no-caret>
    <template slot="header">
      <span> {{ name }} </span>
     
    </template>\
    <template slot="dropdown">
      <a><b-dropdown-item><i class="fa fa-user" /> Edit Password</b-dropdown-item></a>
      <a v-on:click="logout()" ><b-dropdown-item><i class="fa fa-lock" /> Logout</b-dropdown-item></a>
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
