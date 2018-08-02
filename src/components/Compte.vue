<template>
<div class='main'>
    <p>hello</p>

    <b-button @click="newRow">+</b-button>
    <table>
        <tr>
            <th>id</th>
            <th>date</th>
            <th>libelle</th>
            <th>prix</th>
        </tr>
        <tr v-for="item in items" :key="item.id">
        <td>{{item.id}}</td>    
        <td><input v-model="item.date"></td>
        <td><input v-model="item.libelle"></td>
        <td><input v-model="item.prix"></td>
        </tr>
    </table>
</div>
       
</template>
<script>
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'
export default {
   name:'Compte',
   data() {
       return{
           items:[
               {
                id:0,
                date: '2018-07-22',
                libelle: 'sandwich',
                prix: '5'
               },
                {
                id:1,
                date: '2018-07-22',
                libelle: 'céréales',
                prix: '3'
               }
            ]
       }
       
   },
   methods:{
       newRow(event){
           this.items.push({
                id:this.items.length,
                date:"new",
                libelle:"new" ,
                prix: "new"
           });
       }

   }

}
</script>
<style>
.main{
    margin-left: 5em;
    margin-right:5em;

}

table {
    font-family: arial, sans-serif;
    border-collapse: collapse;
    width: 100%;
}

td, th {
    border: 1px solid #dddddd;
    text-align: left;
    padding: 8px;
}

tr:nth-child(even) {
    background-color: #dddddd;
}

input{
    border-style:none;
    background-color:inherit;
}
</style>


