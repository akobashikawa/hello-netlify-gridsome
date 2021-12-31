<template>
  <Layout>
    <h1 class="text-xl font-semibold mb-5">Welcome to {{ $static.metadata.siteName }} Blog!</h1>
    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Error doloremque omnis animi, eligendi magni a voluptatum, vitae, consequuntur rerum illum odit fugit assumenda rem dolores inventore iste reprehenderit maxime! Iusto.</p>

    <ul class="list-outside list-disc">
      <li v-for="post in $page.posts.edges" :key="post.path" class="mt-3">
        <g-link :to="post.node.path">{{ post.node.title }} – {{post.node.date}}</g-link>
      </li>
    </ul>
  </Layout>
</template>

<script>
export default {
  metaInfo: {
    title: 'Blog'
  }
}
</script>

<static-query>
	query {
		metadata {
			siteName
		}
	}
</static-query>

<page-query>
  query Posts {
    posts: allPost (sortBy: "date", order: DESC) {
      edges {
        node {
          id
          title
          path
          tags
          date (format: "YYYY-MM-DD")
          description
        }
      }
    }
  }
</page-query>

<style scoped>
</style>