<template>
    <div>
        <button class="btn btn-success">Ajouter</button>
<table class="table table-striped">
    <thead>
        <tr>
            <th>Image</th>
            <th>Nom categorie</th>
            <th>Modifier</th>
            <th>supprimer</th>
        </tr>
    </thead>
        <tbody>
            <tr v-for="cat in categorie" :key="cat.id">
                <td><img :src="cat.imagecategorie" width="80" height="100"></td>
                <td>{{ cat.nomcategorie }}</td>
                <td><button class="btn btn-warning">Modifier</button></td>
                <td><button class="btn btn-danger">Supprimer</button></td>
                
            </tr>
        </tbody>
   
</table>
    </div>
</template>

<script setup>
import {ref,onMounted} from 'vue'
import axios from 'axios'
const categorie=ref([])
const getCategories=async()=>{ 
//pour apporter la liste des categorie
await axios.get("http://localhost:8000/api/categories")
.then(res=>{
    categorie.value=res.data
    
})
.catch(error=>{
    console.log(error)
})
}
onMounted(()=>{
    getCategories()
})
</script>

<style lang="css" scoped>
.table{
    margin-top:30px;
}
</style>