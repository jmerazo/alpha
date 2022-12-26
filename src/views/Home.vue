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
                <option v-for="d in deliverys" :key="d.id">{{d.names + d.last_names}}</option>
            </select>
        </div>
        <div class="form-floating mb-3" id="i-data-guide">
            <input type="password" class="form-control" id="floatingPassword" placeholder="Password">
            <label for="floatingPassword">PAMI</label>
        </div>
        <div class="form-floating mb-3" id="i-data-guide">
            <input v-on:keyup="guideSearch()" type="number" class="form-control" id="floatingInput"
                placeholder="name@example.com">
            <label for="floatingInput">Número de guía</label>
        </div>
    </div>

    <div class="form-table-guide">
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

    </div>
</template>

<script lang="ts">
import axios from "axios"

export default {
    name: "RecaudoMensajeros",
    data(){
        return {
            zona: "",
            guide: "",
            dataGuide: [],
            deliverys: ""
        }
    },
    mounted(){
        this.listDelivery()
    },
    methods: {
        async guideSearch(){
            await axios.get(`https://www3.interrapidisimo.com/ApiServInter/api/Mensajeria/ObtenerRastreoGuias?guias=${this.guide}`, {
                        headers: {
                            "Content-Type": "application/json",
                            "Access-Control-Allow-Origin": "*"
                        }
            })
            .then((Response) => {
                this.dataGuide = this.dataGuide + Response.data;
            });
        },
        async listDelivery(){
            await axios.get(`http://127.0.0.1:5000/api/alpha/delivery/list`, {
                headers: {
                    "Content-Type": "application/json",
                    "Access-Control-Allow-Origin": "*"
                }
            })
            .then((Response) => {
                this.deliverys = Response.data;
            });
        }
    }
}
</script>

<style>
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

.form-table-guide{
    margin: 20px;
}
</style>