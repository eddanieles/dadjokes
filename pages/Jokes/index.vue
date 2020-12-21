<template>
    <div>
        <ul>
            <li v-for="joke in jokes" :key="joke.id">
                <p>{{joke.joke}}</p>
            </li>
        </ul>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    data() {
        return {
            jokes: []
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
                    console.log(data)
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