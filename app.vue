<template>

  <div>


    <v-row >
      <div class='d-flex'>
        <v-col 
          no-gutters>
      
          <v-card 
            width="200" 
            class="pa-5 mt-5 ml-5"
            outlined>
            
            <div width="50">
              {{station}}<br>
              FECAL: {{ stationValues[0] }} <br>
              PH: {{ stationValues[1] }} <br>
              DO: {{ stationValues[2] }}<br>
              TSS: {{ stationValues[3] }} <br>
              TEMPERATURE: {{ stationValues[4] }} <br>
              BOD: {{ stationValues[5] }} <br> 
            
            </div>
            
          </v-card>
      
        </v-col>
  
        <v-col md="9" no-gutters>
          <v-card class="pa-5 ma-5"
            outlined>    
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

            <div>
              <Line :data="data" :options="options" />
            </div>

            <v-btn
              elevation="2"
              @click="getForecast(this.tab , this.station)"
            >predict</v-btn>
          </v-card>

        </v-col>

      </div>
      
    </v-row>
    
    


    <v-card class="pa-5 ma-5" outlined>
      
      <div>
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

      </div>


      <div>
        <v-btn
        elevation="2"
        @click="select(this.tab , 'Station 1')"
      >1</v-btn>
      
      <v-btn
        elevation="2"
        @click="select(this.tab , 'Station 2')"
      >2</v-btn>
      <v-btn
        elevation="2"
        @click="select(this.tab , 'Station 3')"
      >3</v-btn>
      <v-btn
        elevation="2"
        @click="select(this.tab , 'Station 4')"
      >4</v-btn>
      <v-btn
        elevation="2"
        @click="select(this.tab , 'Station 5')"
      >5</v-btn>
      </div>
      

    </v-card>
        


    
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

      
      const url = 'http://0ced-34-124-154-216.ngrok.io/'
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
            label: feature,
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
      const url = 'http://0ced-34-124-154-216.ngrok.io'
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
        console.log(error);
      })

      this.allData = x;
      this.select("pH_Structured_data.csv", this.station);

      
    }

  },
  mounted(){
    this.load();
    
    

  }
}
</script>
