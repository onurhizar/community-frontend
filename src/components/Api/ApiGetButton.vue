<template>
    <button class="btn btn-outline-primary btn-sm" 
    @click="getReq">{{btnText}}</button>
</template>

<script>
import axios from 'axios'
axios.defaults.headers.get["Content-Type"] = "application/json"

export default {
    name: 'ApiGetButton',
    data(){return {
        btnText:"API Get",
        listOfComments:[],
    }},
    
    methods:{
        getReq: async function(){
            let commentList

            await axios.get('http://localhost:8000/api/comments/')
            .then(function(res){
                commentList = res.data
            })
            .catch(function(err){console.log(err)})
            
            this.$emit('guncel',commentList)  // emit a custom event
        }
    },
}
</script>
