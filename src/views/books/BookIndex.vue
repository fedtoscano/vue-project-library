<script>
import axios from 'axios';
export default {
data() {
    return {
        books: []
    }
},
methods:{
        getData(page = 1){
            axios.get('http://127.0.0.1:8000/api/books', {
                params: {
                    page: page,
                },
                })
            .then((response) =>{
                console.log(response)
                this.books = response.data.results.data
            })
            .catch((error)=>{
                //codice
            })
    },
},
created(){
        this.getData()
    },
}
</script>

<template>
<ul>
    <li v-for="book in books">
        {{ book.title }}
    </li>
</ul>
</template>

<style scoped lang="scss">
</style>