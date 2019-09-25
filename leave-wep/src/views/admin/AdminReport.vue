<template>
  <div class="animated fadeIn font col-center">
     
     <b-row class="my-1">
       <div class="card" style="width: 80%;margin-top:5%;">
          <div class="card-header">
            Report
          </div>
          <div class="card-body">
            
            <b-row style="margin-bottom: 5%;">
              <b-card-body class="pb-0">
                <div class="row">
                <b-form @submit="onSubmit">
                <div class="col">
                    <b-dropdown id="dropdown-1" text="เดือน" variant="danger" class="m-md-2">
                      <b-dropdown-item>Feb</b-dropdown-item>
                    </b-dropdown>
                
                    <b-dropdown id="dropdown-1" text="ปี" variant="danger" class="m-md-2">
                      <b-dropdown-item>2019</b-dropdown-item>
                    </b-dropdown>
                
                    <button type="submit" class="btn fontbutton">ค้นหา</button>
                </div>
                </b-form> 
                <div class="col">
                  <b-navbar type="light" style="float:right;">
                    <b-nav-form>
                      <b-form-input class="mr-sm-2" placeholder="Search"></b-form-input>
                      <b-button variant="outline-success" class="my-2 my-sm-0" type="submit">Search</b-button>
                    </b-nav-form>
                  </b-navbar>
                </div>
                </div>
              </b-card-body>
            </b-row>
            
             <b-row>
               <b-card-body class="pb-0">
                 <div class="row">
                   <div class="col">
                    <label >ลาทั้งหมด: </label>
                   </div>
                 </div>
                   <div class="row">
                      <div class="col">
                        <label>ลาพักร้อน:</label>
                      </div>
                      <div class="col">
                        <label>ลากิจ:</label>
                      </div>
                      <div class="col">
                        <label>ลาป่วย:</label>
                      </div>
                    </div>
                </b-card-body>
             </b-row>
             <b-row class="my-1">
              <b-card-body class="pb-0">
                <b-table striped hover :items="items"></b-table>
              </b-card-body>
            </b-row>
           
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
  data() {
      return {
        items: [
          { รหัสพนักงาน: '62xxx', ชื่อ: 'xxxxxx', ประเภทการลา: 'ลาป่วย', วันเริ่มต้น: '23 ก.ย. 62', วันสิ้นสุด: '24 ก.ย. 62', สถานะการลา: 1 },
          { รหัสพนักงาน: '62xxx', ชื่อ: 'xxxxxx', ประเภทการลา: 'ลากิจ', วันเริ่มต้น: '26 ก.ย. 62', วันสิ้นสุด: '27 ก.ย. 62', สถานะการลา: 0 },
          { รหัสพนักงาน: '62xxx', ชื่อ: 'xxxxxx', ประเภทการลา: 'ลาพักร้อน', วันเริ่มต้น: '27 ก.ย. 62', วันสิ้นสุด: '28 ก.ย. 62', สถานะการลา: 0 },
          { รหัสพนักงาน: '62xxx', ชื่อ: 'xxxxxx', ประเภทการลา: 'ลากิจ', วันเริ่มต้น: '28 ก.ย. 62', วันสิ้นสุด: '29 ก.ย. 62', สถานะการลา: 1 }
        ]
      }
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
