<template>
    <h1 class="text-center text-white-50">Comments</h1>

    <div class="container text-center"> 
        <ApiGetButton @guncel="getComments"/>
    </div>

    <CommentsHolder :commentArray="commentList" />
</template>

<script>
import ApiGetButton from '@/components/Api/ApiGetButton'
import ApiDelButton from '@/components/Api/ApiDelButton'
import CommentsHolder from '@/components/CommentsHolder.vue'

export default {
    name: 'Comments',
    components: {
        ApiGetButton,
        ApiDelButton,
        CommentsHolder,
    }, 

    data(){
        return {
            commentList: [],
    }},

    methods: {
        getComments(newList){
            this.commentList = newList // update comment list UI
        },
    },
}
</script>