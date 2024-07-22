<script>
import axios from 'axios';

export default {
  data() {
    return {
      city:"",
      error:"",
      info: null
    }
  },
  computed: {
    cityName() {
      return "<<" + this.city + ">>" 
    },
    showTemp() {
      return "Temperature: " + this.info.main.temp
    },
     showFeelsLike() {
      return "Fells like: " + this.info.main.feels_like
    },
     showMinTemp() {
      return "Minimum Temperature: " + this.info.main.temp_min
    },
    showMaxTemp() {
      return "Maximum Temperature: " + this.info.main.temp_max
    },
  },
  methods: {
    getWeather(){
        if(this.city.trim().length < 2) {
          this.error = "need the name of more than one character : ";
          return false
        }
        this.error = ""

        axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=6f61d436e74b824241bb7eec5a0a51fc`)
             .then (res => (this.info = res.data))
    }
  }
}
</script>

<template>
  <div class="wrapper">
    <h1>Weather App</h1>
    <p>find out the weather in {{ city == "" ? "your city" : cityName }} </p>
    <input type="text" v-model="city" placeholder="city name">
    <button v-if="city !=''" @click="getWeather()">get the weather</button>
    <button disabled v-else>enter the name of the city</button>
    <p class="error">{{ error }}</p>

    <div v-if="info != null">
      
      <p>{{ showTemp }}</p>
      <p>{{ showFeelsLike }}</p>
      <p>{{ showMinTemp }}</p>
      <p>{{ showMaxTemp }}</p>
    </div>
  </div>
</template>

<style scoped>

.error {
color: red;
}
.wrapper {
  width: 900px;
  height: 500px;
  border-radius: 50px;
  padding: 20px;
  background: #27132c;
  text-align: center;
  color:#fff
}
.wrapper h1 {
  margin-top: 50px;
}
.wrapper p {
 margin-top: 20px; 
}
.wrapper input {
 margin-top: 30px;
 background: transparent;
 border-radius: 0;
 border-bottom: 2px solid #110813;
 color: #fcfcfc;
 font-size: 14px;
 padding: 5px 8px;
 outline: none; 
}
.wrapper input:focus {
  border-bottom-color: #6e2d7d;
}
.wrapper button {
 margin-left: 20px;
 background: #e6e2d5;
 border-radius: 10px;
 border: 2px solid #b88e13;
 color: fff;
 padding: 10px 15px;
 cursor:pointer;
 transition: transform 500ms ease;
}
.wrapper button:hover {
  transform: scale(1.1) translateY(-5x);
}
.wrapper button:disabled {
  background: #aa871f;
  cursor: not-allowed;
}
</style>
