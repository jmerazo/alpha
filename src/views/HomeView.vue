<template>
  <div class="form-guide-data">
    <div class="form-floating mb-3 me-3" id="i-data-guide">
      <input type="date" class="form-control" id="floatingInput" placeholder="name@example.com">
      <label for="floatingInput">Fecha</label>
    </div>
    <div class="form-floating" id="i-data-guide">
      <select name="" class="form-control" id="floatingZona">
        <option value="" selected disabled for="floatingZona">Seleccione una zona</option>
        <option value="zona general" for="floatingZona">Zona general</option>
        <option value="zona oriente" for="floatingZona">Zona oriente</option>
        <option value="zona norte" for="floatingZona">Zona norte</option>
        <option value="zona sur" for="floatingZona">Zona sur</option>
      </select>
    </div>
    <div class="form-floating mb-3 me-3" id="i-data-guide">
      <select name="" class="form-control" id="floatingZona">
        <option value="" selected disabled for="floatingZona">Seleccione un mensajero</option>
        <option value="zona general" for="floatingZona">Zona general</option>
      </select>
    </div>
    <div class="form-floating mb-3" id="i-data-guide">
      <input type="password" class="form-control" id="floatingPassword" placeholder="Password">
      <label for="floatingPassword">PAMI</label>
    </div>
    <div class="form-floating mb-3" id="i-data-guide">
      <input v-bind:on-keydown="guide" type="number" class="form-control" id="floatingInput" placeholder="name@example.com">
      <label for="floatingInput">Número de guía</label>
    </div>
  </div>

  <table class="table">
    <thead class="table-dark">
      <tr>
        <th>Número guía</th>
        <th>Destinatario</th>
        <th>Dirección</th>
        <th>Valor transporte</th>
        <th>Valor sobreflete</th>
        <th>Total</th>
        <th>Estado</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td></td>
        <td></td>
        <td></td>
        <td></td>
        <td></td>
      </tr>
    </tbody>
  </table>  
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import navBar from '@/components/NavBar.vue'; // @ is an alias to /src

@Options({
  components: {
    navBar,
  },
  data(){
    return {
      zona: "",
      guide: ""
    }
  }
})
export default class HomeView extends Vue {}
</script>

<style scoped>
.i-data-guide{
  text-align: center;
}

.form-guide-data{
  display: grid;
  grid-template-areas:  "head head"
                        "menu main"
                        "foot foot";
  margin: 20px;
  background-color: antiquewhite;
  justify-content: center;
}
</style>
