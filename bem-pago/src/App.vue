<template>
  <div id="app" class="d-flex justify-content-center" style="width:100%">
    <form-principal/>
  </div>
</template>

<script>
import FormPrincipal from '../src/components/FormPrincipal.vue'
export default {

  components: {
    FormPrincipal
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;700&family=Poppins:ital,wght@0,200;0,400;0,600;1,500;1,600&family=Roboto+Serif:ital,wght@0,300;0,500;1,400&display=swap');

input[type=number]::-webkit-inner-spin-button { 
    -webkit-appearance: none;
    
}
input[type=number] { 
   -moz-appearance: textfield;
   appearance: textfield;

}

 

body {
  font-family: 'Montserrat', sans-serif;
  font-family: 'Poppins', sans-serif;
  font-family: 'Roboto Serif', serif;
  background: #8a2be2;
  padding: 0px;
  margin: 0px;
}
.color-white{
  color: white;
}
.d-flex{
  display: flex !important;
}
.flex-direction-column{
  flex-direction: column !important;
}
.justify-content-center{
  justify-content: center !important;
}
.justify-content-between{
  justify-content: space-between !important;
}
.align-items-center{
  align-items:center !important;
}
.align-items-end{
  align-items:flex-end !important;
}
.container{
  padding: 0 40px 0 40px !important;
}

.container-sm{
  padding: 0 20px 0 20px !important;
}

.btn{
  background: #2f3575;
  color: white;
  border:1px solid #2f3575;
  border-radius: 5px;
  padding: 5px 20px!important;
  margin: 0;
  font-size:16px;
  text-transform: uppercase;
  cursor: pointer;

}

.btn-plus{
  width: 40px;
  height: 40px;
  font-size:30px!important;
  padding: 0 !important;

}

.disabled{
  background: rgb(179, 173, 173);
  border-color: rgb(179, 173, 173);
}

.input-form{
  background: #e5e5e5;
  border: 1px solid #b3b3db;
  max-width: 40px;
  padding: 10px;
  font-size:15px;
}

.card{
  border: 1px solid rgba(189, 188, 188, 0.637);
  border-radius: 5px;
  
}
</style>
