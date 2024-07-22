<script>
export default {
  
}
</script>

<template>
  <div class="wrapper">
    <h1>Weather App</h1>
    <p>find out the weather in your city</p>
    <input type="text" placeholder="city name">
    <button>get the weather</button>
  </div>
</template>

<style scoped>
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
</style>
