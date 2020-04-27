<template>
    <div>
        <div class="row justify-content-center">
            <div class="col-md-6">
                <div class="input-group mb-3">
                    <input type="text" class="form-control">
                    <div class="input-group-append">
                        <button class="btn btn-outline-secondary" type="button">Search</button>
                    </div>
                </div>
            </div>
        </div>

        <div class="row justify-content-center">
            <div class="col-md-8">
                <h4>Post List</h4>
                <div v-for="data in datas" :key="data.id" class="card mb-3">
                    <div class="card-body">
                        <h5 class="card-title">{{ data.title }}</h5>
                        <p class="card-text">{{ data.description }}</p>
                        <h6>{{ data.published ? 'Publish' : 'Unpubish' }}</h6>
                        <a href="#" class="card-link">Edit</a>
                    </div>
                </div>

                <button class="btn btn-sm btn-danger m-3">Delete All</button>
            </div>
        </div>
    </div>
</template>

<script>
import PostService from '../../services/PostService'

export default {
    name: "post-list",

    data(){
        return {
            datas: []
        }
    },

    methods: {
        retrievePosts(){
            PostService.getAll()
            .then((result) => {
                this.datas = result.data
                console.log(result.data)
            }).catch((err) => {
                console.log(err)
            })
        }
    },

    mounted() {
        this.retrievePosts()
    }
}
</script>