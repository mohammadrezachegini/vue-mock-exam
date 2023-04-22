<template>
    <div>
        <h1>Country Population</h1>
        <ul>
            <li>Name: {{ chosenCountry.name }}</li>
        </ul>


        <ul v-if="chosenCountry.length">
            <li v-for="(ct, index) in chosenCountry" :key="index">
                {{ ct }}
            </li>
        </ul>
        <!-- <button >Remove </button> -->
    </div>
</template>

<script>

    export default{
        name: "shoppingList",
        props:{
            chosenCountry: Array
        },
    
        data(){
            return{

                
            }
        },
        methods:{
            // handleRemoveButtton(event){
            //     event.preventDefault();
            //     // this.chosenCountry.pop();
            // }

        },

        mounted(){
        },

        watch:{
            
        }
    }

</script>

<style>

</style>