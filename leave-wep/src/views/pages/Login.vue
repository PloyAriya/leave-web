<template>
<body>
  <div class="app flex-row align-items-center">
    <div class="container">
      <div align="center">
          <img src="https://i.pinimg.com/originals/9a/5c/9d/9a5c9d9096dc9d2dafb3e8051a723435.png" alt="Computer man" style="width:150px;height:150px;"><br/>
          <h1 class="font">Leave System</h1><br/>
      </div>
      <b-row class="justify-content-center">
        <b-col md="8">
          <b-card-group >
            <b-card no-body class="form">
              <b-card-body >
                <b-form>
                  <h1 class="font">Login</h1>
                  <p class="text-muted">Sign In to your account</p>
                  <b-input-group class="mb-3">
                    <b-input-group-prepend><b-input-group-text><i class="icon-user"></i></b-input-group-text></b-input-group-prepend>
                    <b-form-input type="text" class="form-control" placeholder="Username" v-model="username" autocomplete="username" />
                  </b-input-group>
                  <b-input-group class="mb-4">
                    <b-input-group-prepend><b-input-group-text><i class="icon-lock"></i></b-input-group-text></b-input-group-prepend>
                    <b-form-input type="password" class="form-control" placeholder="Password" v-model="password" autocomplete="current-password" />
                  </b-input-group>
                  <b-row>
                    <b-col cols="6">
                      <b-button v-on:click="login()" class="fontbutton">Login</b-button>
                    </b-col>
                  </b-row>
                </b-form>
              </b-card-body>
            </b-card>
          </b-card-group>
        </b-col>
      </b-row>
    </div>
  </div>
</body>  
</template>

<script>
export default {
  name: 'Login',
  data(){
      return {
          username: "",
          password: "",
      }
  },
  methods: {
      async login() {
        var data = await this.getData()
        console.log(data)
        if(this.username != "" && this.password != "") {
          if (data.status === 200) {
            localStorage.token = data.data.token
            localStorage.firstname = data.data.result.firstname
            localStorage.lastname = data.data.result.lastname
            localStorage.username = this.username
            this.$router.push({ path: '/dashboard'})
          } else {
            alert('Username หรือ Password ผิดตรวจสอบใหม่อีกครั้ง')
          }    
        } else {
             alert("กรุณากรอก Username และ Password.");
        }  
      },
      async getData () {
      try {
        var data = await this.axios.post('http://192.168.20.104:3001/api/v1/login',
          {
            username: this.username,
            password: this.password,
            
          }
        )
        return data
      } catch (err) {
        return err
      }
  }  
  },
  
}
</script>

<style>
    body {
      background-color: #fce4ec;
    }
    .font {
      color: #e91e63;
    }
    .fontbutton {
      background-color: #e91e63;
      color: white;
    }
    .fontbutton:hover {
      background-color: #fce4ec;
      color: gray;
    }
</style>
