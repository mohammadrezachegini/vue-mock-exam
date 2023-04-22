<template>
    <div>
        <h1>Country Population</h1>
        <ul>
            <li>Name: {{ countryDetail.name }}</li>
             <li>Population: {{ countryDetail.population }}</li>
        </ul>
        <button @click="closeDeatil" >Close </button>
        <button @click="handleAddButton">Add to cart</button>
        <shopping-list v-if="!showComponent" :chosenCountry="chosenCountry" ></shopping-list>
    </div>
</template>

<script>
    import ShoppingList from './ShoppingList.vue';

    export default{
        name: "CountryDetails",
        components:{
            ShoppingList
        },
        props:{
            countryDetail: Object
        },
    
        data(){
            return{
                chosenCountry: [],
                showComponent:true
            }
        },
        methods:{
            closeDeatil(){
                this.$emit('close-details')
            },
            handleAddButton(event){
                event.preventDefault();
                this.chosenCountry.push(this.countryDetail['name']);
                this.showComponent = false;
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