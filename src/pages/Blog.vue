<template>
  <Layout
    backLinkPath="/" 
    backLinkName="HOME" 
    titleName="BLOG"
  >
    
    <!-- List posts -->
    <div class="posts">
      <PostCard 
        v-for="edge in $page.posts.edges" 
        :key="edge.node.id" 
        :post="edge.node"
      />
    </div>

  </Layout>
</template>

<page-query>
{
  posts: allPost {
    edges {
      node {
        id
        title
        path
        tags {
          id
          title
          path
        }
        date (format: "MMMM D, YYYY")
        timeToRead
        description
        cover_image (width: 770, height: 380, blur: 10)
        ...on Post {
            id
            title
            path
        }
      }
    }
  }
}
</page-query>

<script>
import PostCard from '~/components/PostCard.vue'

export default {
  components: {
    PostCard
  },
  metaInfo: {
    title: 'Blog | '
  }
}
</script>
