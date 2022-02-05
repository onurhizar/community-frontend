<template>
    <PostComment @commentPosted="appendComment" />
    <div v-if="this.commentArray != undefined">
        <div v-for="comment in this.commentArray" :key="comment.id">
            <Comment 
            :_msg="comment.message" :_nick="comment.nickname" 
            :_date="comment.created_at" :_id="comment.id" 
            @cDel="deleteCommentUI" /> <br>  
        </div>
    </div>
</template>

<script>
import Comment from './Comment.vue'
import PostComment from './Others/PostCommentInputField.vue'
export default {

    components:{
        Comment,
        PostComment,
    },

    methods: {
        appendComment(newObject){
            this.commentArray.push(newObject)
        },

        deleteCommentUI(removedID){
            let itemIndex = this.commentArray.map(obj => obj.id).indexOf(removedID)
            this.commentArray.splice(itemIndex, 1) // remove one item only
        },
    },

    props:{commentArray: Array},
}
</script>