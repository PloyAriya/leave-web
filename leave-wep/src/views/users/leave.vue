<template>
  <div class="animated fadeIn font col-center">
     
     <b-row class="my-1">
       <div class="card" style="width: 80%;margin-top:5%;">
          <div class="card-header">
            Leave
          </div>
          <div class="card-body">
            <b-form @submit="onSubmit">
            <b-row style="margin-bottom: 5%;">
              <b-card-body class="pb-0">
                
                  <b-dropdown id="dropdown-1" name="leave_type" text="ประเภท" variant="danger" class="m-md-2">
                    <b-dropdown-item>ลากิจ</b-dropdown-item>
                    <b-dropdown-item>ลาป่วย</b-dropdown-item>
                    <b-dropdown-item>ลาพักร้อน</b-dropdown-item>
                  </b-dropdown>
              </b-card-body>
            </b-row>
            <b-row>
              <b-col sm="1">
                <label for="input-default">จากวันที่</label>
              </b-col>
              <b-col sm="4">
                <b-form-input id="input-default" name="start_date" type="date"></b-form-input>
              </b-col>
              <b-col sm="1">
                <label for="input-default">ถึงวันที่</label>
              </b-col>
              <b-col sm="4">
                <b-form-input id="input-default" name="end_date" type="date"></b-form-input>
              </b-col>
            </b-row>

            <b-row class="btn-mr">
              <b-button type="submit" variant="primary" style="margin-right:10px;">Submit</b-button>
              <router-link to="/dashboard"><b-button type="reset" variant="danger">Cancle</b-button></router-link>
            </b-row>
            </b-form>
          </div>
        </div>
    </b-row>
  </div>
</template>
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.7/umd/popper.min.js" integrity="sha384-UO2eT0CpHqdSJQ6hJty5KVphtPhzWj9WO1clHTMGa3JDZwrnQq4sF86dIHNDz0W1" crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js" integrity="sha384-JjSmVgyd0p3pXB1rRibZUAYoIIy6OrQ6VrjIEaFf/nJGzIxFDsf4x0xIM+B07jRM" crossorigin="anonymous"></script>
<script>

import { Callout } from '@coreui/vue'

export default {
  name: 'dashboard',
  datas: [],
  components: {
    Callout
  },
 
  methods: {
    async getData () {
      var { result } = await this.axios.get('http://192.168.20.104:3001/api/v1/leaves?user_id=0001&month=02&year=2019')
      console.log(result)
        // this.datas = data
    }
  }
}
</script>

<style>
  @import url('https://fonts.googleapis.com/css?family=Kanit&display=swap');
  /* IE fix */
  #card-chart-01, #card-chart-02 {
    width: 100% !important;
  }
  .font {
    font-family: 'Kanit', sans-serif;
  }
  .col-center {
    margin-left: 13%;
  }
  .pr {
    padding-right: 20px;
  }
  .btn-style {
    margin-left: 56%;
    width: 7%;
  }
  .fontbutton {
      background-color: #e91e63;
      color: white;
  }
  .btn-mr {
    margin-top: 5%;
    margin-left: 80%;
  }
  
</style>
