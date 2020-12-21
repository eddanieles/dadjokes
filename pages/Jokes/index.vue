<template>
    <div>
        <SearchJokes v-on:search-text="searchText"/>
        <Joke 
            v-for="joke in jokes" 
            :key="joke.id" 
            :id="joke.id" 
            :joke="joke.joke"
        /> 
    </div>
</template>

<script>
import axios from 'axios'
import Joke from '../../components/Joke'
import SearchJokes from '../../components/SearchJokes'

export default {
    data() {
        return {
            jokes: []
        }
    },
    components: {
        Joke,
        SearchJokes
    },
    methods: {
        async searchText(text) {
            const config = {
            headers: {
                Accept: "application/json"
                }
            }
            
            try {
                let that = this;
                await axios.get(`https://icanhazdadjoke.com/search?term=${text}`, config)
                    .then(data => {
                        that.jokes = data.data.results
                    })
            } catch (error) {
                console.error(error)
            }
        }
    },
    async created() {
        const config = {
            headers: {
                Accept: "application/json"
            }
        }
        
        try {
            let that = this;
            await axios.get("https://icanhazdadjoke.com/search", config)
                .then(data => {
                    that.jokes = data.data.results
                })
        } catch (error) {
            console.error(error)
        }
    }
}
</script>

<style>

</style>