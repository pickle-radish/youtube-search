<template>
    <div>
        <div>  
            <input @keypress.enter="search" type="text" v-model="searchValue">
        </div>
        <div>
        </div>
        <!-- <ul>
            <li v-for="(result, idx) in results" :key="result.id.videoId" >
                <div>
                    <iframe width="560" height="320" v-if="idx===0" :src="whatchURL+result.id.videoId"></iframe>
                </div>
                <img :src="result.snippet.thumbnails.default.url" alt="">
            </li>
        </ul> -->
    </div>
</template>

<script>

export default {
    name: 'SearchBar',
    data(){
        return{
            searchValue:'',
            results: [],
            
        }
    },
    props:{
        value:String
    },
    methods:{
        search(){
            console.log(this.searchValue)
            this.$emit('inputEnter', this.searchValue)
        },
    }

}
</script>

<style>

</style>