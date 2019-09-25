<template>
  <div class="animated fadeIn font col-center">
    <b-row style="margin-bottom: 5%; margin-top: 2%;">
      <b-card-body class="pb-0">
         <label class="font" style="margin-right:2%;">เดือน</label>
        <b-form-select v-model="selected" :options="options" name="month" style="width:10%;">เดือน</b-form-select>
         
          <!-- <b-dropdown id="dropdown-1" text="เดือน" variant="danger" class="m-md-2">
            <b-dropdown-item>Feb</b-dropdown-item>
          </b-dropdown> -->
        <label class="font" style="margin-right:2%; margin-left: 2%;">ปี</label>
        <b-form-select v-model="selected" :options="options" name="year" style="width:10%;">ปี</b-form-select>
        
          <!-- <b-dropdown id="dropdown-1" text="ปี" variant="danger" class="m-md-2">
            <b-dropdown-item>2019</b-dropdown-item>
          </b-dropdown> -->
        <b-button v-b-modal.modal-prevent-closing class="fontbutton btn-style">ลา</b-button>
        <!-- <router-link to="/leave"><button type="button" class="btn fontbutton btn-style">ลา</button></router-link> -->

        <b-modal
          id="modal-prevent-closing"
          ref="modal"
          title="Leave"
          @show="resetModal"
          @hidden="resetModal"
          @ok="handleOk"
          
        >
        <form ref="form" @submit.stop.prevent="handleSubmit">
          <b-form-group
            
            label="จากวันที่"
            label-for="start_date"
            invalid-feedback="start date is required"
            class="font"
          >
          <b-form-input
            type="date"
            id="start_date"
            required
          ></b-form-input>
          </b-form-group>
          <b-form-group
            
            label="ถึงวันที่"
            label-for="end_date"
            invalid-feedback="end date is required"
            class="font"
          >
          <b-form-input
          type="date"
            id="end_date"
            required
          ></b-form-input>
        </b-form-group>
      </form>
    </b-modal>
      </b-card-body>
    </b-row>
    <b-row>
      <!-- ลากิจ 1 ลาป่วย 2 พักร้อน 3-->
      <b-col sm="4" lg="3">
        <b-card no-body style="background-color: #FEC9C9;">
          <b-card-body class="pb-0">
            <h4 class="mb-0">ลาพักร้อน</h4>
            <p>Vacation Leave</p>
            <p>ลา {{result["3"]}} วัน</p>
            <!-- <span>{{datas}}</span> -->
          </b-card-body>
          <!-- <card-line1-chart-example chartId="card-chart-01" class="chart-wrapper px-3" style="height:70px;" :height="70"/> -->
          <card-line3-chart-example chartId="card-chart-03" class="chart-wrapper" style="height:70px;" height="70"/>

        </b-card>
      </b-col>
      <b-col sm="6" lg="3">
        <b-card no-body style="background-color: #FEC8D8;">
          <b-card-body class="pb-0">
            <h4 class="mb-0">ลากิจ</h4>
            <p>Personal Leave</p>
            <p>ลา {{result["1"]}} วัน</p>
          </b-card-body>
          <card-line3-chart-example chartId="card-chart-03" class="chart-wrapper" style="height:70px;" height="70"/>
        </b-card>
      </b-col>
      <b-col sm="6" lg="3">
        <b-card no-body style="background-color: #FEC9C9;">
          <b-card-body class="pb-0">
            <h4 class="mb-0">ลาป่วย</h4>
            <p>Sick Leave</p>
            <p>ลา {{result["2"]}} วัน</p>
          </b-card-body>
          <card-line3-chart-example chartId="card-chart-03" class="chart-wrapper" style="height:70px;" height="70"/>
        </b-card>
      </b-col>
    </b-row>

    <b-card style="width: 75%;">
      <b-row>
        <b-col sm="5">
          <h4 id="traffic" class="card-title mb-0">การลาใน 1 ปี</h4>
          <div class="small text-muted">
            <li>
              ลาพักร้อน 4 วัน
            </li>
            <li>
              ลากิจ 0 วัน
            </li>
            <li>
              ลาป่วย 2 วัน
            </li>
          </div>
        </b-col>
      </b-row>
    </b-card>
    <b-card style="width: 75%;">
      <b-row>
        <b-col sm="5">
          <h4 id="traffic" class="card-title mb-0">เงื่อนไขการลา</h4>
          <div class="small text-muted">
            <li>
              ลาพักร้อนได้ติดต่อกันไม่เกิน 5 วัน สูงสุด 20 วันต่อปี
            </li>
            <li>
              ลากิจได้ 5 วันต่อปี   
            </li>
          </div>
        </b-col>
      </b-row> 
    </b-card>
  </div>
</template>
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.7/umd/popper.min.js" integrity="sha384-UO2eT0CpHqdSJQ6hJty5KVphtPhzWj9WO1clHTMGa3JDZwrnQq4sF86dIHNDz0W1" crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js" integrity="sha384-JjSmVgyd0p3pXB1rRibZUAYoIIy6OrQ6VrjIEaFf/nJGzIxFDsf4x0xIM+B07jRM" crossorigin="anonymous"></script>
<script>
import CardLine1ChartExample from './dashboard/CardLine1ChartExample'
import CardLine2ChartExample from './dashboard/CardLine2ChartExample'
import CardLine3ChartExample from './dashboard/CardLine3ChartExample'
import CardBarChartExample from './dashboard/CardBarChartExample'
import MainChartExample from './dashboard/MainChartExample'
import SocialBoxChartExample from './dashboard/SocialBoxChartExample'
import CalloutChartExample from './dashboard/CalloutChartExample'
import { Callout } from '@coreui/vue'

export default {
   mounted () {
    this.getData()
    this.getDate()
  },
  name: 'dashboard',
  components: {
    Callout,
    CardLine1ChartExample,
    CardLine2ChartExample,
    CardLine3ChartExample,
    CardBarChartExample,
    MainChartExample,
    SocialBoxChartExample,
    CalloutChartExample
  },
  data: function () {
    return {
      selected: 'Month',
      options: [],
      datas: [],
      result: ""
    }
  },
  methods: {
    async getData () {
      await this.axios.get('http://192.168.20.104:3001/api/v1/leaves?user_id=0001&month=02&year=2019').then((response) => {
        this.datas = response.data
        this.result = this.datas.result[0]
        console.log(this.result)
        // console.log(this.datas.result)
      })
    
    },
    async getDate () {
      await this.axios.get('http://192.168.20.104:3001/api/v1/leaves/month')
      .then( function(res){
        this.options = response.data
        console.log(this.options)
      })
      .catch( function(error){
        console.log('Error: ', error);
      })
    },
    resetModal() {
        this.start_date = ''
        
    },
    handleOk(bvModalEvt) {
        // Prevent modal from closing
        bvModalEvt.preventDefault()
        // Trigger submit handler
        this.handleSubmit()
    },
    handleSubmit() {
        // Exit when the form isn't valid
        if (!this.checkFormValidity()) {
          return
        }
        // Push the name to submitted names
        this.submittedNames.push(this.name)
        // Hide the modal manually
        this.$nextTick(() => {
          this.$refs.modal.hide()
        })
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
    margin-left: 39%;
    width: 7%;
  }
  .fontbutton {
      background-color: #e91e63;
      color: white;
  }
  
</style>
