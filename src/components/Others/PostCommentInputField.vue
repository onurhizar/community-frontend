<template>
    <div class="container text-center">
        <div class="form-group">
            <input v-model="_thecomment" type="text"
            class="form-control" placeholder="Enter your comment"
            @keyup.enter="makePostRequest(_thecomment)">
        </div>

        <button class="btn btn-outline-secondary btn-sm" 
        @click="makePostRequest(_thecomment)">{{btnText}}</button>
    </div>
</template>

<script>
import axios from 'axios'
axios.defaults.headers.get["Content-Type"] = "application/json"

export default {
    data(){
        return{
            btnText: "Post Comment",
            _thecomment: "",
    }},

    methods:{
        async makePostRequest(text){
            if (text != ""){ // if input field is not empty..
                let postData = { // prepare the javascript object for post request for API
                    nickname: "tester1",
                    message: text
                }
                let responseStatus
                let _inserted 
                await axios.post('http://localhost:8000/api/comments/', postData)
                .then(function(res){
                    responseStatus = res.status // 201 if it is successful
                    _inserted = res.data // API sends back the inserted object
                })
                .catch(function(err){console.log(err)}) // FOR DEBUGGING
                if (responseStatus == 201) {
                    this._thecomment = "" // reset the input field
                    this.$emit('commentPosted', _inserted) // emit event to append obj to cmmnt list
                }
            }
        }
    }
}
</script>