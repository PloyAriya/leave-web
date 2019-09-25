<template>
    <AppHeader fixed style="background-color: #F9B3BC; height: 70px !important;">
      <!-- <SidebarToggler class="d-lg-none" display="md" mobile /> -->
      <b-link class="d-flex">
        <img class="navbar-brand-auto" src="https://i.pinimg.com/originals/9a/5c/9d/9a5c9d9096dc9d2dafb3e8051a723435.png" width="50" height="50" alt="CoreUI Logo">
      </b-link>
      <b-navbar-nav class="d-flex">
        <b-nav-item class="p-3" to="/dashboard">Home</b-nav-item>
        <b-nav-item class="p-3" to="/history" exact>History</b-nav-item>
        <b-nav-item v-if ="check_type === '2'" class="p-3"  >Confirm Leave</b-nav-item>
        <b-nav-item class="p-3" to="/#" hidden>Confirm Leave</b-nav-item>
        <b-nav-item v-if ="check_type === '2'" class="p-3" >Report</b-nav-item>
        <b-nav-item class="p-3" to="/#" hidden>Report</b-nav-item>
      </b-navbar-nav>
      <b-navbar-nav class="ml-auto">
        <b-nav-item><DefaultHeaderDropdownAccnt/></b-nav-item>
        <b-nav-item></b-nav-item>
      </b-navbar-nav>
    </AppHeader>
</template>
<script>
import { Header as AppHeader, SidebarToggler, AsideToggler } from '@coreui/vue'
import DefaultHeaderDropdownAccnt from './DefaultHeaderDropdownAccnt'

export default {
  name: 'DefaultHeader',
  components: {
    AsideToggler,
    AppHeader,
    DefaultHeaderDropdownAccnt,
    SidebarToggler
  },
  data: () => {
    return { 
        itemsCount: 42,
        check_type: localStorage.role
    }
  }
}
</script>
