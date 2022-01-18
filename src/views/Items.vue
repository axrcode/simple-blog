<template>
    <div class="container">
        <div class="row">
            <div class="col-md-8 mx-auto">
                <div class="card bg-light p-3">
                    <div class="card-body">
                        
                        <div class="row">
                            <div class="col-md-6 text-start mb-3">
                                <label for="name">Nombre:</label>
                                <input 
                                    type="text" 
                                    class="form-control"
                                    v-model="item.name"
                                >
                            </div>

                            <div class="col-md-3 text-start mb-3">
                                <label for="quantity">Cantidad:</label>
                                <input 
                                    type="number" 
                                    class="form-control"
                                    v-model="item.quantity"
                                >
                            </div>

                            <div class="col-md-3 text-start mb-3">
                                <label for="price">Precio:</label>
                                <input 
                                    type="number" 
                                    step="0.01"
                                    class="form-control"
                                    v-model="item.price"
                                >
                            </div>

                            <div class="col-md-12 text-start mb-5">
                                <label for="description">Descripción:</label>
                                <input 
                                    type="text" 
                                    class="form-control"
                                    v-model="item.description"
                                >
                            </div>

                            <div class="col-md-12 text-start d-grid gap-2">
                                <button 
                                    class="btn btn-outline-success"
                                    @click="saveItem()"
                                >
                                    Guardar Producto
                                </button>
                            </div>
                        </div>

                    </div>
                </div>
            </div>

            <div class="col-12 mt-5">
                <div class="card bg-light p-3">
                    <div class="card-body">
                        <table class="table">
                            <thead class="table-light">
                                <th>ID</th>
                                <th>NOMBRE</th>
                                <th>PRECIO</th>
                                <th>CANTIDAD</th>
                                <th>DESCRIPCION</th>
                                <th>ACCIONES</th>
                            </thead>
                            <tbody>
                                <tr v-for="item in list_items" :key="item.id">
                                    <td>{{ item.id }}</td>
                                    <td>{{ item.name }}</td>
                                    <td>{{ item.price }}</td>
                                    <td>{{ item.quantity }}</td>
                                    <td>{{ item.description }}</td>
                                    <td></td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    data() {
        return {
            list_items: [],
            item: {
                name: '',
                price: 0,
                quantity: 0,
                description: ''
            }
        }
    },
    mounted() {
        this.listItems()
    },
    methods: {
        async listItems() {
            const {data} = await axios.get('http://laravue.test/api/items')
            this.list_items = data
        },
        async saveItem() {
            await axios.post('http://laravue.test/api/items', this.item)
            this.listItems()
        },
        updateItem() {

        },
        deleteItem() {
            
        }
    }
}

</script>
