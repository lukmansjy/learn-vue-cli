<template>
    <div>
        <form @submit.prevent>
            <div class="form-group">
                <label for="title">Title</label>
                <input type="text" id="title" class="form-control" v-model="post.title">
            </div>
            <div class="form-group">
                <label for="desc">Description</label>
                <textarea id="desc" cols="10" rows="4" class="form-control" v-model="post.description"></textarea>
            </div>
            <button class="btn btn-success" @click="postSubmit()">Submit</button>
        </form>
    </div>
</template>

<script>
import PostService from '../../services/PostService'
export default {
    name: "post-add",
    data() {
        return {
            post: {
                id: null,
                title: "",
                description: "",
                published: false
            }
        }
    },

    methods: {
        postSubmit(){
            let data = {
                title: this.post.title,
                description: this.post.description
            }

            PostService.create(data)
                .then(result => {
                    this.post.id = result.data.id
                    console.log(result)
                    this.$router.push({ name: 'posts'})
                }).catch( err => {
                    console.log(err)
                })
            
        }
    }
}
</script>