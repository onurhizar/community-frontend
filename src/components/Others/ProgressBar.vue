<template>
    <button class="btn btn-primary">comment</button>
    <div class="container">
        <div class="progress">
        <div class="progress-bar" role="progressbar" 
        style="width: {{this.percent}}%" aria-valuenow="{{this.percent}}" 
        aria-valuemin="0" aria-valuemax="100"></div>
    </div>
</div>
</template>

<script>
export default {
    data(){return{
        percent:75,
    }
},

}
</script>
