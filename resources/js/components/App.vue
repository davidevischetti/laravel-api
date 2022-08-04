<template>
<div class="container">
    <h1 class="text-center">Boolpress</h1>
    <div class="row g-2">
        <div v-for="post in posts" :key="post.id"  class="col-sm-6 col-md-4">
            <div class="card h-100">
                <img :src="post.image" :alt="post.title" class="card-img-top">
                <div class="card-body d-flex flex-column">
                    <h5 class="card_title">{{post.title}}</h5>
                    <p class="card-text mb-auto">{{post.content}}</p>
                    <a :href="baseUrl + '/posts/' + post.slug" class="btn btn-primary mt-3">link</a>
                </div>
            </div>
        </div>
    </div>
    <nav aria-label="...">
        <ul class="pagination pagination-lg mt-5">
            <li class="page-item active" aria-current="page">
            <span class="page-link">1</span>
            </li>
            <li class="page-item"><a class="page-link" href="#">2</a></li>
            <li class="page-item"><a class="page-link" href="#">3</a></li>
        </ul>
    </nav>
</div>
</template>

<script>

export default {
    name: 'App',

    data () {
        return {
            baseUrl: window.location.origin,
            posts: []
        }
    },

    created() {
        axios.get('http://localhost:8000/api/posts')
            .then(response => {
                this.posts = response.data.data;
                console.log(response);
            })
            .catch(error => console.log('error'));
    }
}
</script>

<style lang="scss" scoped>
    @import 'bootstrap/scss/bootstrap';
</style>

