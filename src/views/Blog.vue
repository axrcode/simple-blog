<template>
    <div class="container">
        <div class="row mb-4">
            <h1 class="fw-bold">My Blog</h1>
            <h2 class="fst-italic">{{ texto }}</h2>
        </div>

        <div class="row">
            <div class="col-md-3 offset-md-3 d-grid gap-2">
                <button
                    class="btn btn-secondary" 
                    @click="cambiarTitulo()">
                    Cambiar Titulo
                </button>
            </div>
            <div class="col-md-3">
                <select class="form-select">
                    <option :key="lenguaje" v-for="lenguaje in lenguajes">
                        {{ lenguaje }}
                    </option>
                </select>
            </div>
        </div>

        <div class="row pb-5">
            <Card v-for="(item, index) in data" :key="index" :articulo="item"></Card>
        </div>
    </div>
</template>

<script>
    import Card from '@/components/Card'
    import axios from 'axios'

    export default {
        components: {
            Card
        },
        data() {
            return {
                titulo: true,
                texto: 'Información de noticias para el Blog',
                lenguajes: ['JavaScript', 'PHP', 'Java', 'Python', '.NET'],
                data: [],
            }
        },
        mounted() {
        
        },
        async created() {
            const {data} = await axios.get('https://dev.to/api/articles')
            this.data = data
        },
        methods: {
            cambiarTitulo() {
                if ( this.titulo == true ) {
                this.texto = 'Más Información de noticias para el Blog'
                } else {
                this.texto = 'Información de noticias para el Blog'
                }
                this.titulo = !this.titulo
            }
        }
    }
</script>
