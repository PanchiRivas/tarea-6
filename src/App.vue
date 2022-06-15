<template>
<div id="page">
  <div id="app">
    <b-navbar class="navBar">
      <img src="../src/assets/task.png" class="d-inline-block align-top" id="notelogo" alt="notes logo">
      <h1 id="titlenav" >My notes</h1>
    </b-navbar>
      
    <b-container class="mt-5">
      <b-row>
        <b-col cols="8" lg="7" md="7">
          <h1 id="titleList">Shopping list</h1>
        </b-col>
        <b-col cols="4" lg="5" md="5">
          <img src="../src/assets/shopping-bag.png" id="notelogo" alt="notes logo">
        </b-col>
      </b-row>
      <!--Hasta aca titulo -->

      <div class="home">
        <div>
          <b-row class="mt-5">
          <b-col cols="12" lg="7">
            <p class="mt-5">Articulo</p>
            <b-form-input type="text" v-model="nuevaFruta" v-on:keyup.enter="agregarFruta"></b-form-input>
          </b-col>
          
          <b-col cols="12" lg="5">
            <p class="mt-5">Cantidad</p>
            <b-form-input type="number" v-model.number="cantidadFruta" v-on:keyup.enter="agregarFruta"></b-form-input>
          </b-col>

        </b-row>
        <br>
        <div id="articulos" >
          <b-button id="boton" variant="success" v-on:click="agregarFruta">Agregar</b-button> <!--v-on: se puede cambiar por @-->
        </div>
        
<!-- listado por pantalla-->
        </div>
        <div id="listado" class="mt-3">
          <ul class="mt-3">
          <li v-for="fruta of frutas" v-bind:key="fruta">
           
            {{fruta.nombre}} 
            <b-button variant="danger" @click="fruta.cantidad--"> - </b-button>
            {{fruta.cantidad}}
            <b-button variant="success" @click="fruta.cantidad++"> + </b-button>
            <span v-if="fruta.cantidad < 0"> Tienes valores negativos!</span>
          </li>
        </ul>
        </div>
      </div>
    </b-container>
  </div>
</div>
</template>

<script>

export default {
  data(){
    return{
      frutas: [{nombre: 'Manzana', cantidad: 0},
        {nombre: 'Pera', cantidad: 5},
        {nombre: 'Uva', cantidad: 2}],
        nuevaFruta: '',
        cantidadFruta: ''
    }
  },
  methods:{
    agregarFruta(){
      this.frutas.push({
        nombre: this.nuevaFruta, cantidad: this.cantidadFruta
      });
      this.nuevaFruta='';
      this.cantidadFruta= null;
    }
  }
}
</script>

<style scoped>

#page{
  background-color: #EBEBEB;
  height: 100vh;
}
.navBar{
  background-color: #CEF5F3;
  box-shadow: 2px 2px 2px 1px rgba(0, 0, 0, 0.2);
}
#notelogo{
  width: 50px;
  margin-left: 5%;
}
#titlenav{
  text-align: center;
  width: 100%;
  font-size: 40px;
  margin-right: 10%;
}
#titleList{
  text-align: right;
}

.home{
  background-color: white;
  padding-left: 5%;
  padding-right: 5%;
  padding-bottom: 5%;
  border-radius: 30px;
}
#articulos{
  text-align: center;
}
#boton{
  padding-left: 40px;
  padding-right: 40px;
}

ul{
  list-style-type: none;
}
#listado{
  background-color: #CEF5F3;
  border-radius: 30px;
  padding-top: 2%;
  padding-left: 5%;
  padding-right: 5%;
  padding-bottom: 3%;
}

</style>
