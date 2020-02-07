<template>
  <nuxt-link
     :to="id">
     <div class="card text-center" style="width: 18rem;">
      <img :src="thumbnailImage" class="card-img-top" :alt="title" :title="title">
      <div class="card-body">
        <h5 class="card-title">{{title}}</h5>
        <p class="card-text">{{excerpt}}</p>
        <a href="#" class="btn btn-primary">Go somewhere</a>
      </div>
    </div>
    </nuxt-link>
</template>

<script>
export default {
  name: 'PostReview',
  props: {
    title: {
      type: String,
      required: true
    },
    excerpt: {
      type: String,
      required: true
    },
    thumbnailImage: {
      type: String,
      required: true
    },
    id: {
      type: String,
      required: true
    }
  }
}
</script>
