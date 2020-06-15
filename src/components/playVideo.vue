<template>
    <div>
        <iframe width="560" height="320" :src="whatchURL+playId"></iframe>
    </div>
</template>

<script>
export default {
    name:'playVideo',
    data(){
        return{
            whatchURL: "https://www.youtube.com/embed/",
        }
    },
    props:{
        result:Object,
        playId:String
    }
}
</script>

<style>

</style>