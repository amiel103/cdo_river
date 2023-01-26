<template>

    <div>
        <v-card class="ma-5 pa-5">

            <v-tabs
              v-model="station"
              bg-color="#0BE1E3"
            >
              <div
                class="d-flex justify-center mb-6">

              <v-tab 
                value='Station 1'
              >'Station 1'</v-tab>

              <v-tab 
                value='Station 2'
              >'Station 2'</v-tab>

              <v-tab 
                value='Station 3'
              >'Station 3'</v-tab>

              <v-tab 
                value='Station 4'
              >'Station 4'</v-tab>

              <v-tab 
                value='Station 5'
              >'Station 5'</v-tab>

              </div>
            
            </v-tabs>

        <div v-if="station =='Station 1'">
            <v-text-field
            label="PH"
            v-model="send1PH"
            outlined
          ></v-text-field>
          
          <v-text-field
            label="BOD"
            v-model="send1BOD"
            outlined
          ></v-text-field>
          <v-text-field
            label="DO"
            v-model="send1DO"
            outlined
          ></v-text-field>
          <v-text-field
            label="FECAL"
            v-model="send1FECAL"
            outlined
          ></v-text-field>
          <v-text-field
            label="TSS"
            v-model="send1TSS"
            outlined
          ></v-text-field>
          <v-text-field
            label="TEMPERATURE"
            v-model="send1TEMPERATURE"
            outlined
          ></v-text-field>
        </div>
        
        <div v-if="station =='Station 2'">
            <v-text-field
            label="PH"
            v-model="send2PH"
            outlined
          ></v-text-field>
          
          <v-text-field
            label="BOD"
            v-model="send2BOD"
            outlined
          ></v-text-field>
          <v-text-field
            label="DO"
            v-model="send2DO"
            outlined
          ></v-text-field>
          <v-text-field
            label="FECAL"
            v-model="send2FECAL"
            outlined
          ></v-text-field>
          <v-text-field
            label="TSS"
            v-model="send2TSS"
            outlined
          ></v-text-field>
          <v-text-field
            label="TEMPERATURE"
            v-model="send2TEMPERATURE"
            outlined
          ></v-text-field>
        </div>

        <div v-if="station =='Station 3'">
            <v-text-field
            label="PH"
            v-model="send3PH"
            outlined
          ></v-text-field>
          
          <v-text-field
            label="BOD"
            v-model="send3BOD"
            outlined
          ></v-text-field>
          <v-text-field
            label="DO"
            v-model="send3DO"
            outlined
          ></v-text-field>
          <v-text-field
            label="FECAL"
            v-model="send3FECAL"
            outlined
          ></v-text-field>
          <v-text-field
            label="TSS"
            v-model="send3TSS"
            outlined
          ></v-text-field>
          <v-text-field
            label="TEMPERATURE"
            v-model="send3TEMPERATURE"
            outlined
          ></v-text-field>


        </div>

        <div v-if="station =='Station 4'">
            <v-text-field
            label="PH"
            v-model="send4PH"
            outlined
          ></v-text-field>
          
          <v-text-field
            label="BOD"
            v-model="send4BOD"
            outlined
          ></v-text-field>
          <v-text-field
            label="DO"
            v-model="send4DO"
            outlined
          ></v-text-field>
          <v-text-field
            label="FECAL"
            v-model="send4FECAL"
            outlined
          ></v-text-field>
          <v-text-field
            label="TSS"
            v-model="send4TSS"
            outlined
          ></v-text-field>
          <v-text-field
            label="TEMPERATURE"
            v-model="send4TEMPERATURE"
            outlined
          ></v-text-field>


        </div>

        <div v-if="station =='Station 5'">
            <v-text-field
            label="PH"
            v-model="send5PH"
            outlined
          ></v-text-field>
          
          <v-text-field
            label="BOD"
            v-model="send5BOD"
            outlined
          ></v-text-field>
          <v-text-field
            label="DO"
            v-model="send5DO"
            outlined
          ></v-text-field>
          <v-text-field
            label="FECAL"
            v-model="send5FECAL"
            outlined
          ></v-text-field>
          <v-text-field
            label="TSS"
            v-model="send5TSS"
            outlined
          ></v-text-field>
          <v-text-field
            label="TEMPERATURE"
            v-model="send5TEMPERATURE"
            outlined
          ></v-text-field>


        </div>

        <div v-if="station =='Station 6'">
            <v-text-field
            label="PH"
            v-model="send6PH"
            outlined
          ></v-text-field>
          
          <v-text-field
            label="BOD"
            v-model="send6BOD"
            outlined
          ></v-text-field>
          <v-text-field
            label="DO"
            v-model="send6DO"
            outlined
          ></v-text-field>
          <v-text-field
            label="FECAL"
            v-model="send6FECAL"
            outlined
          ></v-text-field>
          <v-text-field
            label="TSS"
            v-model="send6TSS"
            outlined
          ></v-text-field>
          <v-text-field
            label="TEMPERATURE"
            v-model="send6TEMPERATURE"
            outlined
          ></v-text-field>


        </div>
        <v-btn @click="sendData()">send data</v-btn>

        
        <NuxtLink to="/app">
            
            <v-btn>back</v-btn>

        </NuxtLink>

        </v-card>
  

        
        
      
      
    </div>
    
      
    
    
  </template>
  
  <script>
  import axios from 'axios'
  
  export default {
    
    data() {
      return {
        
        send1PH:'',
        send1BOD:'',
        send1DO:'',
        send1FECAL:'',
        send1TSS:'',
        send1TEMPERATURE:'',
        send2PH:'',
        send2BOD:'',
        send2DO:'',
        send2FECAL:'',
        send2TSS:'',
        send2TEMPERATURE:'',
        send3PH:'',
        send3BOD:'',
        send3DO:'',
        send3FECAL:'',
        send3TSS:'',
        send3TEMPERATURE:'',
        send4PH:'',
        send4BOD:'',
        send4DO:'',
        send4FECAL:'',
        send4TSS:'',
        send4TEMPERATURE:'',
        send5PH:'',
        send5BOD:'',
        send5DO:'',
        send5FECAL:'',
        send5TSS:'',
        send5TEMPERATURE:'',
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
    
      
      
  
      async sendData(){

        
        const data = {
          "station":'a',
          "data":[{
            "BOD_Structured_data":[this.send1BOD,this.send2BOD,this.send3BOD,this.send4BOD,this.send5BOD],
            "DO_Structured_data":[this.send1DO,this.send2DO,this.send3DO,this.send4DO,this.send5DO],
            "Fecal_Structured_data":[this.send1FECAL,this.send2FECAL,this.send3FECAL,this.send4FECAL,this.send5FECAL],
            "pH_Structured_data":[this.send1PH,this.send2PH,this.send3PH,this.send4PH,this.send5PH],
            "Temperature_Structured_data":[this.send1TEMPERATURE,this.send2TEMPERATURE,this.send3TEMPERATURE,this.send4TEMPERATURE,this.send5TEMPERATURE],
            "TSS_Structured_data":[this.send1TSS,this.send2TSS,this.send3TSS,this.send4TSS,this.send5TSS]
          }]
        }
  
        const headers = { 'content-type': 'application/json' , 'Access-Control-Allow-Origin' : '*'};
        await axios.post('http://127.0.0.1:8000/addData' ,data , headers).then(function (response) {
          console.log("done")  
        }).catch(function(error) {
          console.log(" error" )
          console.log(error)
        })
  
        this.$router.go(-1)
      }
  
    }
  }
  </script>