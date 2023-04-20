<template>
    <div>
        <h1>Country Population</h1>
        <ul>
            <li>Name: {{ countryDetail.name }}</li>
             <li>Population: {{ countryDetail.population }}</li>
        </ul>
        <button @click="closeDeatil" >Close </button>
    </div>
</template>

<script>

    export default{
        name: "CountryDetails",
        props:{
            countryDetail: Object
        },
    
        data(){
            return{

            }
        },
        methods:{
            closeDeatil(){
                this.$emit('close-details')
            }
        },

        mounted(){
            // console.log("PROPS: ", this.props.id)
        },

        watch:{
            
        }
    }

</script>

<style>

</style>