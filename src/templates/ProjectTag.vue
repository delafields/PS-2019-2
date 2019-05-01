<template>
  <Layout backLinkPath='/projects' backLinkName='PROJECTS'>
    <h1 class="tag-title text-center space-bottom">
      # {{ $page.projectTag.title }}
    </h1>

    <div class="projects">
      <ProjectCard 
        v-for="edge in $page.projectTag.belongsTo.edges" 
        :key="edge.node.id" 
        :project="edge.node"
      />
    </div>
  </Layout>
</template>

<page-query>
query ProjectTag ($id: String!) {
  projectTag (id: $id) {
    title
    belongsTo {
      edges {
        node {
          ...on ProjectPost {
            title
            path
            date (format: "D. MMMM YYYY")
            timeToRead
            description
            content
          }
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
  metaInfo () {
    return {
      title: '#' + this.$page.projectTag.title + ' | '
    }
  }
}
</script>

<style lang="scss">
.tag-title {
  text-transform: uppercase;
}

</style>

