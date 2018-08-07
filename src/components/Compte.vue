<template>
<div class='main'>
    <p>hello</p>

    <b-button @click="newRow">+</b-button>
    <b-button @click="rmlastRow">rm last row</b-button>
	<b-button @click="rmallRow">rm all row</b-button>
	<b-button @click="rmoneRow">rm one row</b-button>
	<b-button @click="rmsmRow">rm some row</b-button>
	<b-button @click="numberRow">row number</b-button>
	<b-button @click="addoneRow">add row</b-button>
	<b-button @click="sch">search</b-button>
	<b-button @click="sum">sum</b-button>
	<b-button @click="rfreshRow">refresh</b-button>
    <table>
	    <tr v-for="rmitem in rmitems" :key="rmitem.id">     
            <th>date:</th>
            <th>libelle:</th>
            <th>prix:</th>
        </tr>
	    <tr v-for="rmitem in rmitems" :key="rmitem.id">
		 <td><input v-model="rmitem.date"></td>
        <td><input v-model="rmitem.libelle"></td>
        <td><input v-model="rmitem.prix"></td>
        <b-button @click="rmRow">rm row</b-button>				
		</tr>
	    </br>
		<tr v-for="sumitem in sumitems" :key="sumitem.id">
		 <th> sum:</th>
		 <td>{{sumitem.libelle}}</td> 
		  <td>{{sumitem.sum}}</td> 
          <b-button @click="sum">sum</b-button>		 
		</tr>
		<tr v-for="numitem in numitems" :key="numitem.id">
		 <th> Number:</th>
		 <td>{{numitem.libelle}}</td> 
		  <td>{{numitem.sum}}</td> 
          <b-button @click="numberRow">row number</b-button>		 
		</tr>
		<tr v-for="additem in additems" :key="additem.id">     
            <th>date:</th>
            <th>libelle:</th>
            <th>prix:</th>
        </tr>
	    <tr v-for="additem in additems" :key="additem.id">
		 <td><input v-model="additem.date"></td>
        <td><input v-model="additem.libelle"></td>
        <td><input v-model="additem.prix"></td>
        <b-button @click="addRow">add row</b-button>				
		</tr>
		</br>
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
            ],
			sumitems:[
              
            ],
			rmitems:[
              
            ],
			numitems:[
              
            ],
			additems:[
              
            ],
			schitems:[
              
            ],
			rmv:''
       }
       
   },
   methods:{
       newRow(event){
           this.items.push({
                id:this.items.length,
                date:"new",
                libelle:"new" ,
                prix: 'new'			
           });
       },
	   newrmRow(evt){
           this.rmitems.push({
                id:this.rmitems.length,
                date:"write date",
                libelle:"write libelle" ,
                prix: 'write prix'			
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
	   
	   rmRow(evt){
				   for(var i = 0 ; i <= this.items.length ; i++) {
				       if ((this.items[i].libelle == this.rmitems[0].libelle) && (this.items[i].date == this.rmitems[0].date) && (this.items[i].prix == this.rmitems[0].prix)){
					     evt.preventDefault();
                         alert(JSON.stringify("date: "+this.items[i].date + " libelle: "+ this.items[i].libelle + " prix: "+ this.items[i].prix));
					     this.items.splice(
							i,
                            1							
					     );
						  break;
					   }
					   
				     }
				   
				   
       },
	   rmoneRow(evt){
	              if ((this.rmitems.length == 0)){
	                this.newrmRow(evt);
				   }
				   if ((this.rmitems.length == 1)){
				    this.rmitems.splice(
							this.rmitems
                            						
					     );
	                this.newrmRow(evt);
				   }
				   
       },
	   sum(evt){
		   var leprix = 0;
           for(var i = 0 ; i < this.items.length ; i++) {
                  if (this.items[i].prix != ''){		   
				     leprix = leprix + parseInt(this.items[i].prix);
                    }
				}
				
              if ((this.sumitems.length == 0)){
			    this.sumitems.push({
						id:this.sumitems.length,
						sum:leprix,
						libelle: 'Sum is:'
				   });		
			  }
			  
			 if ((this.sumitems.length == 1)){
			    this.sumitems.splice(
							this.sumitems
                            						
					     );
			    this.sumitems.push({
						id:this.sumitems.length,
						sum:leprix,
						libelle: 'Sum is:'
				   });			
             }			          			     
       },
	   numberRow(evt){
	             var number = this.items.length;
				 var p = this.numitems.length;
		        if ((p == 0)){
			         this.numitems.push({
						id:p,
						sum:number,
						libelle: 'Row Number is:'
				   });	
			   }
			   if ((p == 1)){
			    this.numitems.splice(
							this.numitems
                            						
					     );
			    this.numitems.push({
						id:p,
						sum:number,
						libelle: 'Row Number is:'
				   });	
			    		
             }	
                
       },
	   addoneRow(evt){
				 var p = this.additems.length;
		        if ((this.additems.length == 0)){
			         this.additems.push({
						id:p,
						date:'ecrit date',
						libelle: 'ecrit libelle',
						prix: 'ecrit prix'
				   });	
			   }
			   if ((p == 1)){
			    this.additems.splice(
							this.additems
                            						
					     );
			    this.additems.push({
						id:p,
						date:'ecrit date',
						libelle: 'ecrit libelle',
						prix: 'ecrit prix'
				   });	
			    		
             }	
                
       },
	   addRow(evt){
				 var p = this.items.length;
				 var ladate = this.additems[0].date;
				 var lelibelle = this.additems[0].libelle;
				 var leprix = this.additems[0].prix;
			     this.items.push({
						id:p,
						date:ladate,
						libelle: lelibelle,
						prix: leprix
				   });	   
       },
	   rfreshRow(evt){
           if ((this.sumitems.length == 0)){
			    
			  }
			  
			 if ((this.sumitems.length == 1)){
			    this.sumitems.splice(
							this.sumitems
                            						
					     );
			    		
             }
             if ((this.rmitems.length == 0)){
			    
			  }
			  
			 if ((this.rmitems.length == 1)){
			    this.rmitems.splice(
							this.rmitems
                            						
					     );
			    		
             }	
            
             if ((this.numitems.length == 0)){
			    
			  }
			  
			 if ((this.numitems.length == 1)){
			    this.numitems.splice(
							this.numitems
                            						
					     );
			    		
             }

             if ((this.additems.length == 0)){
			    
			  }
			  
			 if ((this.additems.length == 1)){
			    this.additems.splice(
							this.additems
                            						
					     );
			    		
             }					 
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


