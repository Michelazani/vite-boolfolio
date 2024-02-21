<template lang="">
    <main class="container">
        <section class="row">
            <div class="col-12">
                <h3>Our projects</h3>
                <ul>
                    <li v-for="portfolio in portfolios" :key="portfolio.id">
                        {{ portfolio.Project }}
                    </li>
                </ul>
            </div>
        </section>
    </main>
</template>
<script>
import axios from 'axios';

export default {
    name:'AppMain',
    data(){
        return{
            portfolios: [],
        }
    },
    methods:{
        getPortfolios(){
            axios.get('http://127.0.0.1:8000/api/portfolios', {
                params: {
                }
            })
            .then((response) => {
                console.log(response.data.results.data);
                // mi serve il this. per poter accedere ai data
                this.portfolios = response.data.results.data;

            })
            .catch(function (error) {
                console.warn(error);
                this.$router.push({ name: 'not-found' })
            })
        }
    },
    created(){
        this.getPortfolios();
    }

}
</script>
<style lang="">
    
</style>