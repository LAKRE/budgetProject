<template>
<div class='main'>
    <p>hello</p>

    <b-button @click="newRow">+</b-button>
    <b-button @click="rmlastRow">rm last row</b-button>
	<b-button @click="rmRow">rm one row</b-button>
	<b-button @click="rmallRow">rm all row</b-button>
	<b-button @click="sum">sum</b-button>
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
                prix: 5
               },
                {
                id:1,
                date: '2018-07-22',
                libelle: 'céréales',
                prix: 3
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
       },
	   
	   rmlastRow(event){
           this.items.splice(
                this.items.length-1,
                1    
           );
       },
	   
	  rmallRow(event){
             for(var i = 0 ; i < this.items.length ; i++) {
				     this.items.splice(
							this.items[i]
					   ); 
				}		    
       },
	   
	   rmRow(event){
				   for(var i = 0 ; i < this.items.length ; i++) {
				       if (this.items[i].libelle == 'rmv'){
					     this.items.splice(
							this.items[i].id,
							1						
					     );
					   }
				   }
				   
       },
	   sum(event){
		   var leprix = 0;
           for(var i = 0 ; i < this.items.length ; i++) {
                  if (this.items[i].prix != ''){		   
				     leprix = leprix + this.items[i].prix;
					 
                    }
				}	
            this.items.push({
						id:this.items.length,
						date:"date",
						libelle:"sum" ,
						prix: leprix
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


