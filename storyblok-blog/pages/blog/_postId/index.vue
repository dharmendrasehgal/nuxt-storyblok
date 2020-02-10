<template>
  <div class="PostIdComponent">
    <section>
      <!-- Main jumbotron for a primary marketing message or call to action -->
      <div class="jumbotron">
        <div class="container">
          <h1 class="display-3">{{ title }}</h1>
          <p>{{ summary }}</p>
          <p><a class="btn btn-primary btn-lg" href="/blog" role="button">Go Back</a></p>
        </div>
      </div>

      <div class="container">
        <!-- Example row of columns -->
        <div class="row">
          <div class="col-md-12">
            <h2>{{ title }}</h2>
            <p>{{ previewText }}</p>
          </div>
        </div>

        <hr>

      </div>
    </section>
  </div>
</template>

<script>
export default {
  asyncData(context) {
    return context.app.$storyapi.get('cdn/stories/post/' + context.params.postId)
    .then((res) => {
      return {
            id: res.data.story.content._uid,
            title: res.data.story.content.title,
            previewText: res.data.story.content.description,
            thumbnailUrl: res.data.story.content.image,
            summary: res.data.story.content.summary
      };
    })
    .catch(err => {
      console.log('err: ',err);
    })
  }
}
</script>

<style>

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
.container {
  display: block !important;
}
</style>
