<script setup>
import {ref} from 'vue';
const header =ref ( 'App lista de compras')
const items = ref([
{id: 1, label: '10 bolillos'},
{id: 2, label: '1 lata de frijoles'},
{id: 3, label: '1 lata de atún'},
]);
const newItem = ref ('');
const newItemPriority = ref (false);
</script>

<template>
 <h1><i class="material-icons shopping-cart-icon">local_mall</i>{{header}}</h1>
 <div class="add-item form">
    <!--Input de nuevo articulo-->
    <input v-model.lazy="newItem" type="text" placeholder="Ingresar nuevo articulo">
    <!--check Boxes-->
    <label >
       <input v-model ="newItemPriority" type="checkbox">
       Alta prioridad 
   </label>
    {{newItemPriority ? "🔥" : "🧊"}}
    <!--Button-->
    <button v-on:click="items.push({id: items.lenght +1, label: newItem})" class="btn btn-primary">Salvar articulo</button>
 </div>
 <ul>
    <li v-for="{ id, label} in items" v-bind:key="id">
    {{label}}
    </li>
 </ul>
</template>

<style scoped>
.shopping-cart-icon{
font-size: 2rem;}
</style>
