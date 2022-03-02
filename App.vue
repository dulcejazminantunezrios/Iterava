<template>
    <div>
        <h1>{{ bienvenida }}</h1>
        <table align="center">
            <tbody>
                <th>Nombre</th>
                <th>Región</th>
                <th>Población</th>
                <th>Bandera</th>
                <tr v-for="todo in todos" :key="todo.id">
                    <td>{{ todo.name.common }}</td>
                    <td>{{ todo.region }}</td>
                    <td>{{ todo.population }}</td>
                    <td> {{ todo.flags.svg }} </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
import axios from 'axios';
export default{
    data(){
        return{
            bienvenida:'Bienvenido a Iterava.\n Tu guía turistico de bolsillo',
            todos:null
        }
    },
    mounted() {
        console.log('Hola mundo desde mounted')
        this.getTodos();
    },
    methods: {
        getTodos(){
            console.log('Aca va el codigo de get todos')
            axios.get('https://restcountries.com/v3.1/all')
            .then(response => {
                console.log(response)
                this.todos = response.data
            })
            .catch(e=>console.log(e))
            }   
    },
}
</script>

<style>
table, td, th {
  border: 1px solid;
  border-collapse: collapse;
  border-color: rgb(52, 95, 238);
  font-family: Arial, Helvetica, sans-serif;
  align-items: center;
  align-content: center;
  text-align: center;
}
body{
    background-image: './fondo.jpg';
}
h1{
 text-align: center;
 font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}
</style>