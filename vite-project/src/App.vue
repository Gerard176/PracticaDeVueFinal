<script setup>
  import { ref } from 'vue';
  var valorNumerico = ref('')
  var operacion = ref('')
  var num1
  const agregarNumero = (numero) =>{
    valorNumerico.value += numero
  }
  const sumar = () =>{
    num1 = +valorNumerico.value
    valorNumerico.value = ''
    operacion.value = '+'
  }
  const darResultado =() =>{
    var num2 = +valorNumerico.value
    valorNumerico.value = ''
    console.log(operacion)
    if(operacion.value == '+'){ 
      var resultado = num1+num2 
      valorNumerico.value = resultado.toString()
    }else if(operacion.value == '-'){
      var resultado = num1-num2 
      valorNumerico.value = resultado.toString()
    }else if(operacion.value == '/'){
      var resultado = num1/num2 
      valorNumerico.value = resultado.toString()
    }

    var nuevaOperacion = {num1:num1,num2:num2,operacion:operacion.value,resultado:resultado}

    historial.value.push(nuevaOperacion)
    
  }
  const restar = () =>{
    num1 = +valorNumerico.value
    valorNumerico.value = ''
    operacion.value = '-'
  }
  const dividir = () =>{
    num1 = +valorNumerico.value
    valorNumerico.value = ''
    operacion.value = '/'
  }

  const borrar = ()=>{
    valorNumerico.value = ''
  }
  const borrarTodo =()=>{
    valorNumerico.value=''
    historial.value=[]
  }
  var historial = ref([
    
  ])
  
</script>

<template>
 
    <div for="contenedor-general" class="bg-slate-300 h-60 justify-center mt-24 py-4 mx-auto w-1/4 rounded-md">
    <input type="text" class="h-10 w-72 mx-6 rounded-md" v-model="valorNumerico">
    <div for="caja-de-botones" class="mx-6 my-2 flex">
      <div for="caja-de-numeros" class="w-40">
        <button @click="agregarNumero('7')" class="bg-slate-400 py-3 px-3 hover:bg-slate-500">
        7
      </button>
      <button @click="agregarNumero('8')"  class="bg-slate-400 py-3 px-3 hover:bg-slate-500">
        8
      </button>
      <button @click="agregarNumero('9')"  class="bg-slate-400 py-3 px-3 hover:bg-slate-500">
        9
      </button>
      <br>
      <button @click="agregarNumero('4')"  class="bg-slate-400 py-3 px-3 hover:bg-slate-500">
        4
      </button>
      <button @click="agregarNumero('5')"  class="bg-slate-400 py-3 px-3 hover:bg-slate-500">
        5
      </button>
      <button @click="agregarNumero('6')"  class="bg-slate-400 py-3 px-3 hover:bg-slate-500">
        6
      </button>
      <br>
      <button @click="agregarNumero('1')"  class="bg-slate-400 py-3 px-3 hover:bg-slate-500">
        1
      </button>
      <button @click="agregarNumero('2')"  class="bg-slate-400 py-3 px-3 hover:bg-slate-500">
        2
      </button>
      <button @click="agregarNumero('3')"  class="bg-slate-400 py-3 px-3 hover:bg-slate-500">
        3
      </button>
      </div>
      <div for="operaciones" class="mx-3">
        <button @click="dividir()" class="bg-slate-400 py-3 px-3 hover:bg-slate-500">
        /
      </button>
      <button @click="restar()"  class="bg-slate-400 py-3 px-3 hover:bg-slate-500">
        -
      </button>
      <button @click="sumar()"  class="bg-slate-400 py-3 px-3 hover:bg-slate-500">
        +
      </button>
      <button @click="darResultado()"  class="bg-slate-400 py-3 px-3 hover:bg-slate-500">
        =
      </button>
      <button @click="borrar()"  class="bg-slate-400 py-3 px-3 hover:bg-slate-500">
        C
      </button>
      <button @click="borrarTodo()"  class="bg-slate-400 py-3 px-3 hover:bg-slate-500">
        CE
      </button>
      

      </div>
    </div>
    

  </div>
    <div class="bg-slate-950 text-[#ffffff94] rounded-md w-1/4 justify-center mx-auto h-40 px-3 py-3">
      <label class="font-bold">HISTORIAL</label>
      <div v-for="(operacionRealizada,index) in historial" :key="index">
        {{ operacionRealizada.num1 }}{{ operacionRealizada.operacion }}{{ operacionRealizada.num2 }} = {{ operacionRealizada.resultado }}
        <br>
      </div>
    </div> 
   
  
  
  
  

</template>

<style scoped>

</style>
