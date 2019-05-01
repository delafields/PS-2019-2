<template>
  <Layout
    backLinkPath="/" 
    backLinkName="HOME" 
    titleName="PROJECTS"
  >
         
    <!-- List posts -->
    <div class="posts">
      <ProjectCard 
        v-for="edge in $page.projects.edges" 
        :key="edge.node.id" 
        :project="edge.node"
      />
    </div>

  </Layout>
</template>

<page-query>
{
  projects: allProjectPost {
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
        ...on ProjectPost {
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
import ProjectCard from '~/components/ProjectCard.vue'

export default {
  components: {
    ProjectCard
  },
  metaInfo: {
    title: 'Projects | '
  }
}
</script>

<style lang="scss" scoped>
.posts {
  display: grid; 
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  grid-gap: 2rem;
}
</style>
