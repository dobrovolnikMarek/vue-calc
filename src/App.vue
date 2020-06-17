<template>
  <div id="app">
    <input type="text" id="form" @keyup.enter="res">
         <div class="row1">
            <button @click="insert('%')" class="act"><i class="fas fa-percentage"></i></button>
            <button @click="sqrt" class="act"><i class="fas fa-square-root-alt"></i></button>
            <button @click="sqr" class="act"><i class="fas fa-superscript"></i></button>
            <button  @click="insert('1/')" class="act"><sup>1</sup>/<sub>X</sub></button>
         </div>
         <div class="row2">
          <button @click="clean" class="act"><i class="fab fa-cuttlefish"></i></button> 
            <button @click="delEl" class="act"><i class="fas fa-backspace"></i></button>   
            <button @click="insert('/')" class="act"><i class="fas fa-divide"></i></button> 
         </div>
         <div class="row3">
            <button @click="insert(7)" class="num">7</button>
            <button @click="insert(8)" class="num">8</button>
            <button @click="insert(9)" class="num">9</button>
            <button @click="insert('*')" class="act"><i class="fas fa-times"></i></button>
         </div> 
         <div class="row4">
              <button @click="insert(4)" class="num">4</button>
              <button @click="insert(5)" class="num">5</button>
              <button @click="insert(6)" class="num">6</button>
              <button @click="insert('-')" class="act"><i class="fas fa-minus"></i></button>
         </div>  
         <div class="row5">
            <button @click="insert(1)" class="num">1</button>
            <button @click="insert(2)" class="num">2</button>
            <button @click="insert(3)" class="num">3</button>
            <button @click="insert('+')" class="act"><i class="fas fa-plus"></i></button>
         </div>
         <div class="row6">
           <button @click="negate" class="act">&plusmn;</button>
            <button @click="insert(0)" class="num">0</button>
            <button @click="insert('.')" class="act">.</button>
            <button @click="res" class="act"><i class="fas fa-equals"></i></button>
         </div>        
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      el: 0,
    }
  },
  methods:{
    insert: function (num) {
      document.getElementById("form").value += num;
    },
    clean: function(){
      document.getElementById("form").value = "";
    },
    delEl: function(){
      this.el = document.getElementById("form").value;
      document.getElementById("form").value = this.el.substring(0, this.el.length-1);
    },
    res(){
      if(document.getElementById("form").value){
        document.getElementById("form").value= eval(document.getElementById("form").value);
      }
    },
    sqrt(){
        document.getElementById("form").value=Math.sqrt(document.getElementById("form").value);
    },
    sqr(){
      document.getElementById("form").value*=document.getElementById("form").value;
    },
    negate(){
      document.getElementById("form").value=-document.getElementById("form").value;
    } 
  }
}
</script>

<style>
#app{
  text-align: center;
  margin: 10px;
}

body{
  background-color: #000;
}

*{
  margin: 0;
  padding: 0;
}

input{
  text-align: right;
  font-family: 'Roboto Mono', monospace;
  height: 50px;
  font-size: 25px;
  background-color: #000;
  border: 1px solid #fff;
  color: #fff;
}

button{
  width: 75px;
  height: 30px;
  padding: 5px;
  margin: 2px;
  border:none;
  font-size: 20px;
}

input:focus, button:focus{
  outline: none;
}

.row1 button:last-child{
  font-size: 15px;
  font-weight: bolder;
}

.row2 button:nth-child(2){
  width: 158px;
}

.num{
  background-color: #202020;
}

.act{
  background-color: #333333;
}

.num, .act{
  color:#f5f5f5;
}
</style>
