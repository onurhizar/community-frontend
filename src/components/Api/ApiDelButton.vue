<template>
    <button class="btn btn-warning" @click="delReq">Delete</button>
</template>

<script>
import axios from 'axios'
axios.defaults.headers.get["Content-Type"] = "application/json"

export default {
    name: 'ApiDelButton',
    data(){
        return {
        }
    },
    
    methods:{
        async delReq(){
            if (this._id){
                let isStatus204 = false
                await axios.delete('http://localhost:8000/api/comments/'+this._id+'/')
                .then(function(res){
                    //console.log(res.status)     // 204 means deleted
                    isStatus204 = res.status == 204
                })
                .catch(function(err){
                    console.log(err)
                })

                if(isStatus204){
                    this.$emit('commentDeleted')
                }
            }
        }
    },

    props: {
        _id: Number,
    }
}
</script>
