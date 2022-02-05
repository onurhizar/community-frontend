<template>
    <nav class="navbar navbar-expand-sm navbar-dark bg-dark">
        <div class="container-fluid">
            <router-link to="/" class="navbar-brand">
                <img v-if="navbarIconPath" :src="navbarIconPath">
                {{brand}}
            </router-link>

            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
                <div class="navbar-nav">
                    <router-link to="/" class="nav-link">Home</router-link>
                    <router-link to="/comments" class="nav-link">Comments</router-link>
                    <router-link to="/about" class="nav-link">About</router-link>
                </div>
            </div>
        </div>
    </nav>
</template>

<script>
export default {
    props: ['brand', 'navbarIconPath'],
}
</script>