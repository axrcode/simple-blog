<template>
    <div class="col-4 mt-5">
        <a :href="articulo.url" class="text-decoration-none text-black">
            <div class="card shadow">
                <img :src="articulo.social_image" class="card-img-top">
                <div class="card-body">
                    <h5 class="card-title font-weight-bold">
                        {{ articulo.title }}
                    </h5>
                    <p class="card-text">{{ articulo.description }}</p>
                    <p class="card-text">{{ articulo.readable_publish_date }}</p>
                    <p class="card-text">{{ articulo.user.name }} <b>({{ articulo.user.username }})</b> </p>
                </div>
        </div>
        </a>
    </div>
</template>

<script>
    export default {
        props: {
            articulo: Object
        }
    }
</script>

<style>

</style>