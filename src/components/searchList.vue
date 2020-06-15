<template>
    <div>
        <div v-for="result in results" :key="result.id.videoId">
            <img :src="result.snippet.thumbnails.default.url" alt="" >
        </div>
    </div>
</template>

<script>
export default {
    name:'searchList',
    props:{
        results:Array
    },
    methods:{
        videoClick(){
            this.$emit()
        }
    }

}
</script>

<style>

</style>