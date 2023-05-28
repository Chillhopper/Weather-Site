




<html lang="en">
  <head>
    <style>

      :root{  
        --modif: 0;
      }
      
      .generic{
        color: rgb(92, 0, 191);
      }
      
      .weather{
        color: blue;
        font-size: 10x;
        /* text-align: center; */
      }
      
      .container{
        display: flex;
        grid-template-columns: repeat(2, 1fr);
      }
      
      .dino{
      
        width: 300px;
        height: 350px;
        border-style: solid;
        border-width: 5px;
        margin-right: 10px;
      
      }
      
      .stats{
        width: 900px;
        height: 350px;
        border-style:solid;
        border-width: 5px;
        float:left;
        margin-right: 10px;
        
      }
      
      .bottom{
      
        /* margin-top: calc(-350px + var(--modif)); */
        margin-top: -350px;
        width: 1183px;
        height: 300px;
        border-style:solid;
        border-width: 5px;
        
      }
      
      .ads{
        width: 300px;
        /* height: calc(710px - var(--modif)); */
        height: 710px;
        border-style: solid;
        border-width: 5px;
      }
      </style>
  </head>
  <body>
    <div class = "container">

      <!-- <div class = "dino">
        <h1>"hello there, {@html name}!"</h1>
        <img src={image1} alt="A dino" width = "50%">
        <label for="initText" class = "generic">Enter your favourite dino</label>
        <input type = "text" id = "initText" name = "placeholder">
      </div> -->
      
      <div class = "stats">
        <h1 class = "weather">The current temperature is: <span id = "temp"></span></h1>
      </div>
    
      <div class = "ads" ></div>
    
    </div>
    <div class = "bottom">
    </div>

    <script>
      //import axios from 'axios';
      //let name = "<u style=\"color:blue;\">luigi</u>"
      //let image1 = "dino.jpg"
      let apiResponse;
      const tempElement = document.querySelector("#temp");
      
      //const axios = require('axios');
      const lat = 33.44;
      const lon = -94.04;
      const key = `99c042eb03da73b38db5660bf9e9372c`;
      const city = `singapore`;
      const url = `https://api.openweathermap.org/data/3.0/onecall?${lat}&${lon}=-94.04&exclude=hourly,daily&appid=${key}`;//`https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${key}`;
      let data;
      let error;
      let temp;
      
      
      fetch(url).then(response => response.json()).then(Rdata => {
         data = Rdata;
          temp = Rdata.current.temp;
          tempElement.textContent = `${temp}`;
          console.log(Rdata);
        }).catch(err => {error = err ="ERROR"; tempElement.textContent = `${error}`;});
    
      </script>

  </body>


</html>

