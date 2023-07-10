<template>
    <div v-if="job">
        <h1>{{ job.title }}</h1>
        <p>The id is : {{ id }}</p>
        <p>{{ job.details }}</p>
  
    </div>
    <div v-else>
        <p>Loading job data.....</p>

    </div>
</template>

<script>
import Jobs from './Jobs.vue'
export default {
    props: ['id'],
    data(){
        return{
            job:null

        }
    },
    // data(){
    //     return{
    //         id:this.$route.params.id

            
    //     }
    // }
    mounted(){
        fetch('http://localhost:3000/jobs/'+ this.id)
        .then((res) => res.json())
        .then((data) => this.job=data)
        .then((error) => console.log(error.message))


    }

}
</script>

<style>
div h1{
    color: black;
}

</style>