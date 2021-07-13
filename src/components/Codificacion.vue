<template >

  <section class="src-components-codificacion">
    <h5>Ingrese una frase</h5>

   <div class="form-group">
      
    <input 
      type="text" 
      id="text" 
      class="form-control"
      v-model.trim="formData"
    >
    </div>
    
    <pre>Codificado: {{formData|codificado}}</pre>
    <pre>En mayúscula: {{formData|pasarAMayuscula}}</pre>
    <pre>En minúscula: {{formData|pasarAMinuscula}}</pre>
    <pre>Minúscula mayuscula intercalado: {{formData|mayusMinIntercalado}}</pre>
    <pre>Mayuscula minúscula  intercalado: {{formData|minMayusIntercalado}}</pre>


    <p>Respuestas: 1: b  /  2: b  /  3: c  /  4: b  /  5: a</p>

  </section>



</template>

<script lang="js">

  export default  {
    name: 'src-components-codificacion',
    props: [],
    mounted () {

    },
    data () {
      return {
        formData: " "
      }
    },
    methods: {

    },
    computed: {
     
    },
    filters:{
      codificado: function(value){
        return value.toLowerCase().split('').map((caracter) =>{
          if(caracter == 'a'){
            return caracter.replace('a','u')
          }else if(caracter == 'e'){
            return caracter.replace('e','o')
          }else if(caracter == 'o'){
            return caracter.replace('o','e')
          }else if(caracter == 'u'){
            return caracter.replace('u','a')
          }else{
            return caracter
          }      
        }).join('')
        
      },
      pasarAMayuscula: function (value) {
      return value.toUpperCase()
      },
      pasarAMinuscula: function(value){
        return value.toLowerCase()
      },
      mayusMinIntercalado: function(value){
        return value.toUpperCase().split('').map((caracter,index)=>{
          if(index % 2 ===0){
            return caracter.toLowerCase()
          }return caracter
        }).join('')
      },
      minMayusIntercalado: function(value){
        return value.toLowerCase().split('').map((caracter,index)=>{
          if(index % 2 ===0){
            return caracter.toUpperCase()
          }return caracter
        }).join('')
      }

}

  }
</script>

<style scoped lang="css">
  .src-components-codificacion {

  }
</style>
