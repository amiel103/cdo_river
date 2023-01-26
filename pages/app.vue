<template>

  <div >
    
      <h1 class="d-flex justify-center mt-6" > 
        WATER QUALITY MONITORING SYSTEM
      </h1>
    
    <v-row class="d-flex justify-center mb-6">
      <div class='d-flex'>

        <v-col 
          no-gutters>
      
          <v-card 
            width="200" 
            class="pa-5 mt-5 ml-5"
            outlined>
            
            <div width="50">
              {{station}}<br>
<<<<<<< HEAD:pages/app.vue
              BOD: {{ stationValues[0] }} <br>
              DO: {{ stationValues[1] }} <br>
              FECAL: {{ stationValues[2] }}<br>
              PH: {{ stationValues[3] }} <br>
              TEMPERATURE: {{ stationValues[4] }} <br>
              TSS: {{ stationValues[5] }} <br> 
=======
              PH: {{ stationValues[0] }} <br>
              BOD: {{ stationValues[1] }} <br>
              DO: {{ stationValues[2] }}<br>
              FECAL: {{ stationValues[3] }} <br>
              TSS: {{ stationValues[4] }} <br>
              TEMPERATURE: {{ stationValues[5] }} <br> 
>>>>>>> 6d8c5691c27707a064f4b4517915b1873d2af78c:app.vue
            
            </div>
            
          </v-card>
      
        </v-col>
  
        <v-col md="9" no-gutters>

        
          <v-card class="pa-5 ma-5"
            outlined>    

            <v-tabs
              v-model="station"
              bg-color="#0BE1E3"
            >
              <div
                class="d-flex justify-center mb-6">

              <v-tab 
                value='Station 1'
                @click="select(this.tab,this.station)"
              >'Station 1'</v-tab>

              <v-tab 
                value='Station 2'
                @click="select(this.tab,this.station)"
              >'Station 2'</v-tab>

              <v-tab 
                value='Station 3'
                @click="select(this.tab,this.station)"
              >'Station 3'</v-tab>

              <v-tab 
                value='Station 4'
                @click="select(this.tab,this.station)"
              >'Station 4'</v-tab>

              <v-tab 
                value='Station 5'
                @click="select(this.tab,this.station)"
              >'Station 5'</v-tab>

              </div>
            
            </v-tabs>
            
            <v-tabs
              v-model="tab"
              bg-color="#0BE1E3"
            >
              <div
              class="d-flex justify-center mb-6">

              <v-tab 
                value="pH_Structured_data.csv"
                @click="select(this.tab,this.station)"
              >pH</v-tab>

              <v-tab 
                value="BOD_Structured_data.csv"
                @click="select(this.tab,this.station)"
              >BOD</v-tab>

              <v-tab 
                value="DO_Structured_data.csv"
                @click="select(this.tab,this.station)"
              >DO</v-tab>

              <v-tab 
                value="Fecal_Structured_data.csv"
                @click="select(this.tab,this.station)"
              >Fecal</v-tab>

              <v-tab 
                value="TSS_Structured_data.csv"
                @click="select(this.tab,this.station)"
              >TSS</v-tab>

              <v-tab 
                value="Temperature_Structured_data.csv"
                @click="select(this.tab,this.station)"
              >Temperature</v-tab>

              </div>
              
            </v-tabs>
<<<<<<< HEAD:pages/app.vue
            <h1>AA</h1>
=======
            <center><h1>AA</h1></center>
>>>>>>> 6d8c5691c27707a064f4b4517915b1873d2af78c:app.vue
            <div>
              <Line :data="data" :options="options" />
            </div>



            <v-btn
              elevation="2"
              @click="getForecast(this.tab , this.station)"
            >predict</v-btn>
<<<<<<< HEAD:pages/app.vue

            
            <NuxtLink to="/addData">
            
              <v-btn>Add Data</v-btn>

            </NuxtLink>
=======
>>>>>>> 6d8c5691c27707a064f4b4517915b1873d2af78c:app.vue

            
            <v-btn
              elevation="2"
              @click="getForecast(this.tab , this.station)"
            >train Model</v-btn>

<<<<<<< HEAD:pages/app.vue

=======
            <v-dialog
      v-model="dialog"
    >
      <template v-slot:activator="{ props }">
        <v-btn
          color="primary"
          v-bind="props"
          class="ma-5"
        >
          ADD NEW DATA
        </v-btn>
      </template>

      <v-card>
        <v-card-text>
          Add new data to
          {{ station }}
          <v-divider></v-divider>
          <br>
          <v-text-field
            label="PH"
            outlined
          ></v-text-field>
          <v-text-field
            label="BOD"
            outlined
          ></v-text-field>
          <v-text-field
            label="DO"
            outlined
          ></v-text-field>
          <v-text-field
            label="FECAL"
            outlined
          ></v-text-field>
          <v-text-field
            label="TSS"
            outlined
          ></v-text-field>
          <v-text-field
            label="TEMPERATURE"
            outlined
          ></v-text-field>
        </v-card-text>
        
      <v-card-actions>
        <v-btn color="primary" @click="dialog = false">Close</v-btn>
        <v-btn @click="dialog = false">send data</v-btn>
      </v-card-actions>
      </v-card>
    </v-dialog>

            <v-btn
              elevation="2"
              @click="getForecast(this.tab , this.station)"
            >train Model</v-btn>
>>>>>>> 6d8c5691c27707a064f4b4517915b1873d2af78c:app.vue

          </v-card>

        </v-col>

<<<<<<< HEAD:pages/app.vue
=======

          </v-card>

        </v-col>

>>>>>>> 6d8c5691c27707a064f4b4517915b1873d2af78c:app.vue
      </div>
      
    </v-row>
    
  </div>
  
    
  
  
</template>

<script>
import img from '~/assets/map of cdo.png'
import axios from 'axios'
import { Chart, CategoryScale, LinearScale, PointElement, LineElement, Title, Tooltip, Legend } from 'chart.js'
import { Line } from 'vue-chartjs'
Chart.register( CategoryScale, LinearScale, PointElement, LineElement, Title, Tooltip, Legend)
export default {
  name: 'App',
  components: {
    Line
  },
  data() {
    return {
      dialog:false,
<<<<<<< HEAD:pages/app.vue
      sendPH:'',
      sendBOD:'',
      sendDO:'',
      sendFECAL:'',
      sendTSS:'',
      sendTEMPERATURE:'',
=======
>>>>>>> 6d8c5691c27707a064f4b4517915b1873d2af78c:app.vue
      src: img,
      tab: 'pH_Structured_data.csv',
      station: 'Station 1',
      stationValues:[1,2,3,4,5,6],
      data : {
        labels: ['January', 'February', 'March', 'April', 'May', 'June', 'July'],
        datasets: [
          {
            label: 'Data One',
            backgroundColor: '#27A200',
            data: [40, 39, 10, 40, 39, 80, 40]
          }
        ]
      },
      options:{
        responsive: true,
        maintainAspectRatio: false
      },
      allData:[],
    }
  },
  methods:{
  
    async getForecast(feature , station){
      let reqStation
      let forecast
      if(station=='Station 1'){
        reqStation = 1
      }else if(station=='Station 2'){
        reqStation = 2
      }else if(station=='Station 3'){
        reqStation = 3
      }else if(station=='Station 4'){
        reqStation = 4
      }else if(station=='Station 5'){
        reqStation = 5
      }
      
<<<<<<< HEAD:pages/app.vue
      const url = 'http://127.0.0.1:8000/'
=======
      const url = 'http://fbdb-35-221-19-139.ngrok.io/'
>>>>>>> 6d8c5691c27707a064f4b4517915b1873d2af78c:app.vue
      const head = 'getForecast/'+feature+'-'+reqStation
      const req = url+head
      console.log(req)
      const headers = { 'content-type': 'application/json' , 'Access-Control-Allow-Origin' : '*'};
      await axios.get(req,headers)
      .then(function (response) {
        // handle success
        forecast = response['data']
        console.log(response['data'])
      })
      .catch(function (error) {
        // handle error
        console.log(error);
      })
      const aaa = {
        label: feature,
        backgroundColor: 'black',
        data: forecast
      }
      let year=[];
      let y_value = [];
      for (let i = 0; i < this.allData.length; i++) {
        if( feature == Object.keys(this.allData[i])[0] ){
          console.log( this.allData[i][feature].length )
          for (let j = 0; j < this.allData[i][feature].length; j++) {
            year.push(this.allData[i][feature][j]['Year'])
            y_value.push(this.allData[i][feature][j][station])
          }
        }
        } 
      let data = {
        labels: year,
        datasets: [
          {
            label: feature,
            backgroundColor: '#0BE1E3',
            data: y_value
          },
          {
<<<<<<< HEAD:pages/app.vue
            label: 'forecasted values',
=======
            label: 'forcasted',
>>>>>>> 6d8c5691c27707a064f4b4517915b1873d2af78c:app.vue
            backgroundColor: 'black',
            data: forecast
          }
        ]
      }
      
      
      this.data = data
      
    },
    select(feature , station){
      
      console.log(feature)
      let stationValues=[];
      let year=[];
      let y_value = [];
      for (let i = 0; i < this.allData.length; i++) {
        if( feature == Object.keys(this.allData[i])[0] ){
          for (let j = 0; j < this.allData[i][feature].length; j++) {
            year.push(this.allData[i][feature][j]['Year'])
            y_value.push(this.allData[i][feature][j][station])
          }
          
        }
        let last = this.allData[i][ Object.keys(this.allData[i])[0] ]
        console.log( Object.keys(this.allData[i])[0] )
        const value = last.at(-1)[station] 
        
        stationValues.push( value) 
      } 
      
      let data = {
        labels: year,
        datasets: [
          {
            label: feature,
            backgroundColor: '#0BE1E3',
            data: y_value
          }
        ]
      }
      
      this.stationValues = stationValues
      this.data = data
        
      
    },
    async load(){
<<<<<<< HEAD:pages/app.vue
      const url = 'http://127.0.0.1:8000'
=======
      const url = 'http://fbdb-35-221-19-139.ngrok.io'
>>>>>>> 6d8c5691c27707a064f4b4517915b1873d2af78c:app.vue
      const head = '/getAllData'
      let x;
      const headers = { 'content-type': 'application/json' , 'Access-Control-Allow-Origin' : '*'};
      await axios.get(url+head,headers)
      .then(function (response) {
        // handle success
        x = response['data']
        
      })
      .catch(function (error) {
        // handle error
        console.log("error here")
        console.log(error);
      })
      this.allData = x;
      this.select("pH_Structured_data.csv", this.station);
      
    },

    async sendData(){
      const data = {
        'station':this.station,
        "data":[{
          "BOD_Structured_data":this.sendBOD,
          "DO_Structured_data":this.sendDO,
          "Fecal_Structured_data":this.sendFECAL,
          "pH_Structured_data":this.sendPH,
          "Temperature_Structured_data":this.sendTEMPERATURE,
          "TSS_Structured_data":this.sendTSS
        }]
      }

      const headers = { 'content-type': 'application/json' , 'Access-Control-Allow-Origin' : '*'};
      await axios.post('http://127.0.0.1:8000/addData' ,data , headers).then(function (response) {
        console.log("done")  
        this.dialog = false
      }).catch(function(error) {
        console.log(" error" )
        console.log(error)
      })

      
    }

  },
  mounted(){
    this.load();
    
    
  }
}
</script>

<style>
h1.aaa{

}



</style>