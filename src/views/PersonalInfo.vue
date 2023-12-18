<template>
    <div v-if="job">
        <h1>{{job.name}}</h1>
        <p>The job id is:{{id}}</p>
        <p>{{ job.description }}</p> 
    </div>
    <div v-else>
        <p>Loading job details...</p>
    </div>  
</template>
<script>
import axios from 'axios'
export default {
    props:['id'],
    // id:$route.params.id,
    data() {
        return {
            job:null
        }
    },
    mounted(){
        axios.get('http://localhost:3000/jobs/'+ this.id)
        .then(res => this.job = res.data )
        // .then(data => )
        // .catch(err => console.log(err.message))
    }
}
</script>
<style>
    
</style>