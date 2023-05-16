<script>

let name = "<u style=\"color:blue;\">luigi</u>"
let image1 = "dino.jpg"
let apiResponse;
let tempElement = document.querySelector("#temp");

//const axios = require('axios');
import axios from 'axios';
const params = {
  access_key: '0f549269c2c9f91d6bb6b2799fbe98dc',
  query: 'New York City'
}

axios.get('https://api.weatherstack.com/current', {params}).then(response => {
    apiResponse = response.data;
    tempElement = document.querySelector("#temp");
    tempElement.textContent = `${apiResponse.current.temperature}℃`;
    console.log(`Current temperature in ${apiResponse.location.name} is ${apiResponse.current.temperature}℃`);
  }).catch(error => {
    tempElement.textContent = `ERROR`;
    console.log(error);
  });
</script>
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

  margin-top: calc(-350px + var(--modif));
  /* margin-top: -350px; */
  width: 1183px;
  height: 300px;
  border-style:solid;
  border-width: 5px;
  
}

.ads{
  width: 300px;
  height: calc(710px - var(--modif));
  /* height: 710px; */
  border-style: solid;
  border-width: 5px;
}

</style>



<div class = "container">

  <div class = "dino">
    <h1>"hello there, {@html name}!"</h1>
    <img src={image1} alt="A dino" width = "50%">
    <label for="initText" class = "generic">Enter your favourite dino</label>
    <input type = "text" id = "initText" name = "placeholder">
  </div>
  
  <div class = "stats">
    <h1 class = "weather">The current temperature is: <span id = "temp"></span></h1>
  </div>

  <div class = "ads" ></div>

</div>
<div class = "bottom">
</div>

