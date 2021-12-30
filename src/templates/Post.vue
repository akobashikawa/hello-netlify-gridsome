<template>
  <Layout>
    <h1 class="text-xl font-semibold mb-2">{{ $page.post.title }}</h1>
    <span class="font-light">{{ $page.post.date }}</span>
    <div class="mt-8 mb-16 prose lg:prose-lg xl:prose-xl" v-html="$page.post.content" />
  </Layout>
</template>

<page-query>
  query Post($path: String!) {
		post: post(path: $path) {
			title 
			date (format: "YYYY-MM-DD h:mma") 
			content
		}
	}
</page-query>

<script>
export default {
  metaInfo() {
    return {
      title: this.$page.post.title
    };
  }
};
</script>

<style scoped>
</style>