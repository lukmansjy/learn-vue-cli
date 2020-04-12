<template>
  <div>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <a class="navbar-brand" style="cursor: pointer" @click="navigate('posts')">Navbar</a>
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item active">
            <a class="nav-link" style="cursor: pointer" @click="navigate('posts')">Home <span class="sr-only">(current)</span></a>
          </li>
          <li class="nav-item">
            <a class="nav-link" style="cursor: pointer" @click="navigate('post-add')">Post</a>
          </li>
        </ul>
      </div>
    </nav>

    <div class="container mt-3">
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
import router from './router'
export default {
  name: 'App',
  methods: {
    navigate(destRoute){
      if(destRoute !== router.currentRoute.name){
        router.push(destRoute)
      }
    }
  }
}
</script>

