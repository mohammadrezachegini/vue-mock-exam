<template>
    <div>
        <h1>Country Population</h1>
        <ul>
            <li>Name: {{ countryDetail.name }}</li>
             <li>Population: {{ countryDetail.population }}</li>
             <li v-for="(item, index) of countryDetail.hobbies" :key="index">{{ item }}</li>

        </ul>
        <button @click="closeDeatil" >Close </button>
        <!-- <button @click="handleAddButton">Add to cart</button> -->
        <!-- <button @click="handleRemoveButton">Remove to cart</button> -->
        <add-cart :AddCart="handleAddButton"></add-cart>
        <remove-cart :RemoveCart="handleRemoveButton"></remove-cart>    
        <shopping-list v-if="!showComponent" :chosenCountry="chosenCountry" ></shopping-list>
        

    </div>
</template>

<script>
    import ShoppingList from './ShoppingList.vue';
    import AddCart from './AddCart.vue';
    import RemoveCart from './RemoveCart.vue';



    export default{
        name: "CountryDetails",
        components:{
            ShoppingList,
            RemoveCart,
            AddCart
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
            },
            handleRemoveButton(event){
                event.preventDefault();
                // this.chosenCountry.pop();
                this.showComponent = false;

                const itemIndex = this.chosenCountry.indexOf(this.countryDetail['name']);
                this.chosenCountry.splice(itemIndex, 1);


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