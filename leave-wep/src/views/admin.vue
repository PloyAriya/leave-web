<template>
  <div class="animated fadeIn font col-center">
    <b-row style="margin-bottom: 5%;">
      <b-card-body class="pb-0">
        <div class="btn-group pr">
          <button type="button" class="btn btn-light dropdown-toggle" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
            เดือน
          </button>
          <div class="dropdown-menu dropdown-menu-right">
            <button class="dropdown-item" type="button" name="month">----</button>
          </div>
        </div>
        <div class="btn-group pr">
          <button type="button" class="btn btn-light dropdown-toggle" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
            ปี
          </button>
          <div class="dropdown-menu dropdown-menu-right">
            <button class="dropdown-item" type="button" name="year">----</button>
          </div>
        </div>
        <button type="button" class="btn btn-primary">ลา</button>
      </b-card-body>
    </b-row>
    <b-row>
      <b-col sm="4" lg="3">
        <b-card no-body class="bg-primary">
          <b-card-body class="pb-0">
            <h4 class="mb-0">ลาพักร้อน</h4>
            <p>Vacation Leave</p>
            <p>ลา 4 วัน</p>
          </b-card-body>
          <!-- <card-line1-chart-example chartId="card-chart-01" class="chart-wrapper px-3" style="height:70px;" :height="70"/> -->
          <card-line1-chart-example   style="height:70px;" :height="70"/>

        </b-card>
      </b-col>
      <b-col sm="6" lg="3">
        <b-card no-body class="bg-info">
          <b-card-body class="pb-0">
            <h4 class="mb-0">ลากิจ</h4>
            <p>Personal Leave</p>
            <p>ลา 0 วัน</p>
          </b-card-body>
          <card-line2-chart-example chartId="card-chart-02" class="chart-wrapper px-3" style="height:70px;" :height="70"/>
        </b-card>
      </b-col>
      <b-col sm="6" lg="3">
        <b-card no-body class="bg-warning">
          <b-card-body class="pb-0">
            <h4 class="mb-0">ลาป่วย</h4>
            <p>Sick Leave</p>
            <p>ลา 2 วัน</p>
          </b-card-body>
          <card-line3-chart-example chartId="card-chart-03" class="chart-wrapper" style="height:70px;" height="70"/>
        </b-card>
      </b-col>
    </b-row>
    

    <b-card style="width: 75%;">
      <b-row>
        <b-col sm="5">
          <h4 id="traffic" class="card-title mb-0">Traffic</h4>
          <div class="small text-muted">November 2017</div>
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
              ลาพักร้อนได้ติดต่อกันไม่เกิน 5 วัน สูงสุด 20 วันต่อปี
            </li>
            <li>
              ลาพักร้อนได้ติดต่อกันไม่เกิน 5 วัน สูงสุด 20 วันต่อปี
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
      tableItems: [
        {
          avatar: { url: 'img/avatars/1.jpg', status: 'success' },
          user: { name: 'Yiorgos Avraamu', new: true, registered: 'Jan 1, 2015' },
          country: { name: 'USA', flag: 'us' },
          usage: { value: 50, period: 'Jun 11, 2015 - Jul 10, 2015' },
          payment: { name: 'Mastercard', icon: 'fa fa-cc-mastercard' },
          activity: '10 sec ago'
        },
        {
          avatar: { url: 'img/avatars/2.jpg', status: 'danger' },
          user: { name: 'Avram Tarasios', new: false, registered: 'Jan 1, 2015' },
          country: { name: 'Brazil', flag: 'br' },
          usage: { value: 22, period: 'Jun 11, 2015 - Jul 10, 2015' },
          payment: { name: 'Visa', icon: 'fa fa-cc-visa' },
          activity: '5 minutes ago'
        },
        {
          avatar: { url: 'img/avatars/3.jpg', status: 'warning' },
          user: { name: 'Quintin Ed', new: true, registered: 'Jan 1, 2015' },
          country: { name: 'India', flag: 'in' },
          usage: { value: 74, period: 'Jun 11, 2015 - Jul 10, 2015' },
          payment: { name: 'Stripe', icon: 'fa fa-cc-stripe' },
          activity: '1 hour ago'
        },
        {
          avatar: { url: 'img/avatars/4.jpg', status: '' },
          user: { name: 'Enéas Kwadwo', new: true, registered: 'Jan 1, 2015' },
          country: { name: 'France', flag: 'fr' },
          usage: { value: 98, period: 'Jun 11, 2015 - Jul 10, 2015' },
          payment: { name: 'PayPal', icon: 'fa fa-paypal' },
          activity: 'Last month'
        },
        {
          avatar: { url: 'img/avatars/5.jpg', status: 'success' },
          user: { name: 'Agapetus Tadeáš', new: true, registered: 'Jan 1, 2015' },
          country: { name: 'Spain', flag: 'es' },
          usage: { value: 22, period: 'Jun 11, 2015 - Jul 10, 2015' },
          payment: { name: 'Google Wallet', icon: 'fa fa-google-wallet' },
          activity: 'Last week'
        },
        {
          avatar: { url: 'img/avatars/6.jpg', status: 'danger' },
          user: { name: 'Friderik Dávid', new: true, registered: 'Jan 1, 2015' },
          country: { name: 'Poland', flag: 'pl' },
          usage: { value: 43, period: 'Jun 11, 2015 - Jul 10, 2015' },
          payment: { name: 'Amex', icon: 'fa fa-cc-amex' },
          activity: 'Last week'
        }
      ],
      tableFields: {
        avatar: {
          label: '<i class="icon-people"></i>',
          class: 'text-center'
        },
        user: {
          label: 'User'
        },
        country: {
          label: 'Country',
          class: 'text-center'
        },
        usage: {
          label: 'Usage'
        },
        payment: {
          label: 'Payment method',
          class: 'text-center'
        },
        activity: {
          label: 'Activity'
        }
      }
    }
  },
  methods: {
    variant (value) {
      let $variant
      if (value <= 25) {
        $variant = 'info'
      } else if (value > 25 && value <= 50) {
        $variant = 'success'
      } else if (value > 50 && value <= 75) {
        $variant = 'warning'
      } else if (value > 75 && value <= 100) {
        $variant = 'danger'
      }
      return $variant
    },
    flag (value) {
      return 'flag-icon flag-icon-' + value
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
  
</style>
