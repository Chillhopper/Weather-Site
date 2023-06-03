
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
        color: purple;
        font-size: 10x;
        grid-column-start: 1;
        grid-column-end: 3;
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
        border-style:solid;
      }
      
      .bottom{
      
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

      .gridTime{
        display: grid;
        grid-template-columns: auto auto;
        gap: 10px;
        padding: 10px;
        
      }

      .gridTime > div{
        border-style: solid;
        background-color: blue;
        min-height: 100px;
      }

      .item2{
        grid-row-start: 1;
        grid-row-end: 3;
      }

      </style>
  </head>
  <body>
    <div class = "gridTime">
      
      <div>
        <h1 class = "weather">The current temperature in Moscow is: <span id = "temp"></span></h1>
        <button type = "button" id="toK" onclick="getweather()">°K</button>
        <button type = "button" id="toF" onclick="farcon()">°F</button>
        <button type = "button" id="toCel" onclick="celcon()">°C</button>
      </div>
      <div class = "item2"></div>
      <div></div>
    
    </div>

    <script>
      let apiResponse;
      const tempElement = document.querySelector("#temp");
      const celbutton = document.getElementById("tocel");
      
      //const axios = require('axios');

      const urlFree = `http://api.openweathermap.org/data/2.5/forecast?id=524901&appid=de6cd20b072551d7ea89eb5c4cce3e53`;
      let data;
      let error;
      let temp;
      let tempcel;
      let tempfar;
      
      function getweather(){
        fetch(urlFree).then((Rdata) => {console.log("reached 1");return Rdata.json()}).then((jsonres) => {
            console.log("reached 2");
            data = jsonres;
            console.log(data);
            temp = jsonres.list[0].main.temp;
            tempElement.textContent = `${temp.toFixed(1)}°K`;
          }).catch(err => {tempElement.textContent = ` catch activated: ${err}`;}); 
      }

      function celcon(){
        tempcel = (temp - 273.15);
        tempElement.textContent = `${tempcel.toFixed(1)}°C`;
      }
        
      function farcon(){
        tempfar = (temp - 273.15) * 1.8 + 32;
        tempElement.textContent = `${tempfar.toFixed(1)}°F`;
      }
      getweather();
      


      </script>

  </body>


</html>

