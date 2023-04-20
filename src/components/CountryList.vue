<template>
    <div>
        <h1>CountryList</h1>
        <ul v-if="countries.length">
            <li v-for="(ct, index) in countries" :key="index">
                <router-link to="" :id="index" @click="handleCourseClick" >{{ct.name}}</router-link>
            </li>
        </ul>
    </div>

        <country-details  v-if="!showComponent" :countryDetail="countryDetail" @close-details="closeDeatil"></country-details>
      


</template>

<script>
    import CountryDataService from '../service/CountryDataService'
    import CountryDetails from './CountryDetails'

    export default{
        name: "CountryList",
        components:{
            CountryDetails
        },
        data(){
            return{
                countries: [],
                chosenCountry: {},
                countryDetail: {
                    name: "",
                    population:0
                },
                showComponent:true
            }
        },
        methods:{
            closeDeatil(){
                this.showComponent = !this.showComponent
            },

            handleCourseClick(event){
            
            event.preventDefault();
            
            this.availableSections = [];
            this.chosenCountry = this.countries[event.target.id];
            // console.log( this.countries[event.target.id])
            this.countryDetail =  {
                name: this.chosenCountry['name'],
                population: this.chosenCountry['population'],
            }
            console.log(this.countryDetail.population);
            this.showComponent = false
            
        
        },

            retrieveCountries(){
                // this.showComponent = true 
                CountryDataService.getCountries()
                .then(response => {
                    // console.log(response.data);
                    this.countries = response.data;
                })
                .catch(error => {
                    console.log(error);
                })
            }

        },

        mounted(){
            this.retrieveCountries()
            
        

        },

        watch:{

        }
    }

</script>

<style>

</style>