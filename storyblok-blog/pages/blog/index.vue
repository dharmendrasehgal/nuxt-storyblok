<template>
  <div id="container" class="BlogComponent">
    <section v-for="post in posts" :key="post.id">
      <post-review :id="post.slug" :title="post.title" :excerpt="post.previewText" :thumbnailImage="post.thumbnailUrl" />
    </section>
  </div>
</template>

<script>
import PostReview from '@/components/Blog/PostReview';

export default {
  asyncData(context) {
    return context.app.$storyapi.get('cdn/stories', {
      starts_with: 'post/'
    })
    .then((res) => {
      return {
        posts: res.data.stories.map((bp) => {
          return {
            id: bp.content._uid,
            title: bp.content.title,
            previewText: bp.content.summary,
            thumbnailUrl: bp.content.image,
            slug: bp.slug
          };
        })
      }
    })
    .catch(err => {
      console.log('err: ',err);
    })
  },
  components: {
    PostReview
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
#container {
  padding: 2rem;
  display: flex;
  align-item: center;
  justify-content: center;
  xflex-direction: column;
}
#container .card {
  margin: 2rem;
  border: none;
}
</style>
