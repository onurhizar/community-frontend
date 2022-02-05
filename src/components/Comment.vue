<template>
    <div class="container">
        <div class="card text-white bg-dark">
        <div class="card-body">
            <blockquote class="blockquote mb-0">
            <p>{{msg}}</p>
            <footer class="blockquote-footer">{{nickname}}</footer>
            </blockquote> <br>
            <ApiDelButton :_id="this._id" @commentDeleted="$emit('cDel', this._id)" />
        </div>
        </div>
    </div>
</template>

<script>
import ApiDelButton from './Api/ApiDelButton.vue'

export default {
    data(){return{
        msg: this._msg ? this._msg : 'Default comment text..',
        nickname: this._nick ? this._nick : 'Anonymous',
        date: this._date
}},

    props:['_msg', '_nick', '_id', '_date'],

    components:{
        ApiDelButton,
    },
}
</script>
