<script setup>
import {ref} from 'vue';
const header =ref ( 'App lista de compras')
const items = ref([
{id: 1, label: '10 bolillos',purchased: true, highPriority: true},
{id: 2, label: '1 lata de frijoles', purchased: false, highPriority: false},
{id: 3, label: '1 lata de atún',purchased: true, highPriority: true},
]);
//funcion que altera el estado del item
const togglepurchased =(items)=>{  

// invertir la propiedad de "purchased" 
items.purchased =  !item.purchased;
}
//agregando metodo para guardar nuevo articulo en la lista
const saveItem = () => {
items.value.push ({id: items.value.lenght + 1, label: newItem.value}) 
//limpiando el contenido de newItem
newItem.value ="";
};
const newItem = ref ('');
const newItemPriority = ref (false);
const editing =ref (false);
const doEdit = (edit) =>
editing.value = edit;
newItem.value ="";
;
</script>

<template>
   <div class="header">

      <h1><i class="material-icons shopping-cart-icon">local_mall</i>{{header}}</h1>
      <button class="btn">cancelar</button>
      <button class="btn btn-primary">Agregar Articulo</button>
   </div>
 <form v-on:submit.prevent="saveItem" class="add-item form">
    <!--Input de nuevo articulo-->
    <input v-model.trim="newItem" type="text" placeholder="Ingresar nuevo articulo">
    <!--check Boxes-->
    <label >
       <input v-model ="newItemPriority" type="checkbox">
       Alta prioridad 
   </label>
    {{newItemPriority ? "🔥" : "🧊"}}
    <!--Button-->
    <button :disabled="newItem.length=== 0" class="btn btn-primary">Salvar articulo</button>
</form>
 <ul>
    <li 
    v-for="({ id, label, purchased, highPriority},index) in items" 
    v-bind:key="id"
    :class="{strikeout : purchased, priority:highPriority}"
    @click="togglepurchased(items[index])"
    >
    {{ label }}
    </li>
 </ul>
 <p v-if="items.length === 0">🥀 Lista de compras vacia 🥀</p>
 <p v-else>🔥 ingrese mas items 🔥</p>
</template>

<style scoped>
.shopping-cart-icon{
font-size: 2rem;}
</style>
