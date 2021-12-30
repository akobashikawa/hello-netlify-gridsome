<template>
  <Layout>

    <h1 class="text-xl font-semibold mb-5">Pages</h1>
    
    <ul class="list-outside list-disc">
      <li v-for="page in $page.pages" :key="page.path">
        <g-link :to="page.path">{{ page.path }}</g-link>
      </li>
    </ul>
  </Layout>
</template>

<page-query>
  query Pages {
    pages: allPage {
      path
    }
  }
</page-query>

<script>
export default {
  metaInfo: {
    title: 'Pages'
  }
}
</script>

<style>
</style>
