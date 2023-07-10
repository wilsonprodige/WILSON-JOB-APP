<template>
    <h1 class="head">JOBS</h1>
    <div v-if="jobs">
        <div v-for="job in jobs" :key="job.details" :id="job.id" class="job">
            <router-link :to="{ name:'JobDetails', params:{ id: job.id}}">
                <h2>{{ job.title }}</h2>

            </router-link>
        </div>
    </div>
    <div v-else>
        <p>Loading jobs....</p>

    </div>
    
  
</template>

<script>
export default {
    data(){
        return{
            jobs:null
            
        }
    },
    //mounted life cycle hook
    mounted(){
        //using the fetch method
        fetch('http://localhost:3000/jobs')
        .then((res) => res.json())
        .then((data) => this.jobs = data)
        .catch((error) => console.log(error.message))

    }

}
</script>

<style>
.head{
    
    display: inline-block;
    margin: 10px auto;
    min-width: 600px;
}
.job h2{
    background: #f4f4f4;
    padding: 20px;
    border-radius: 10px;
    margin: 10px auto;
    max-width: 600px;
    cursor: pointer;
    color: #444;
}
.job h2:hover{
    background: #ddd;
}
.job a{
    text-decoration: none;
}


</style>