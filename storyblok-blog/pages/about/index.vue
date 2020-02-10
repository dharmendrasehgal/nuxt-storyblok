<template>
  <section id="about-page">
    <h1>{{ title }}</h1>
    <p>{{ description }}</p>
  </section>
</template>

<script>
  export default {
    asyncData(context) {
      return context.app.$storyapi.get('cdn/stories', {
        starts_with: 'about/'
      })
        .then(res => {
          console.log(res.data);
          return {
            blok: res.data.stories[0].content,
            title: res.data.stories[0].content.title,
            description: res.data.stories[0].content.description
          };
        })
        .catch(err => {
          console.log(err);
        });
    }
  }
</script>

<style scoped>
#about-page {
  display: block;
  width: 80%;
  margin: 3rem auto;
}
</style>
