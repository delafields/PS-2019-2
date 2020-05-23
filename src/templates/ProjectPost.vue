<template>
  <Layout backLinkPath='/projects' backLinkName='PROJECTS'>
    <div class="post-title">
      <h1 class="post-title__text">
        {{ $page.project.title }}
      </h1>
      
      <ProjectMeta :project="$page.project" />

    </div>
    
    <div class="post content-box">
      <div class="post__header">
        <g-image 
          alt="Cover image" 
          v-if="$page.project.coverImage" 
          :src="$page.project.coverImage" 
        />
      </div>

      <div class="post__content" v-html="$page.project.content" />

      <div class="post__footer">
        <ProjectTags :project="$page.project" />
      </div>
    </div>

    <div class="post-comments">
      <!-- Add comment widgets here -->
    </div>

    <!--<Author class="post-author" />-->
  </Layout>
</template>

<script>
import ProjectMeta from '~/components/ProjectMeta'
import ProjectTags from '~/components/ProjectTags'
import Author from '~/components/Author.vue'

export default {
  components: {
    Author,
    ProjectMeta,
    ProjectTags
  },
  metaInfo () {
    return {
      title: this.$page.project.title + ' | ',
      meta: [
        {
          name: 'description',
          content: this.$page.project.description
        }
      ]
    }
  }
}
</script>

<page-query>
query ProjectPost ($path: String!) {
  project: projectPost (path: $path) {
    title
    path
    date (format: "MMMM D, YYYY")
    timeToRead
    tags {
      id
      title
      path
    }
    description
    content
  }
}
</page-query>

<style lang="scss">
.post-title {
  padding: calc(var(--space) / 2) 0 calc(var(--space) / 2);
  text-align: center;
}

.post {

  &__header {
    width: calc(100% + var(--space) * 2);
    margin-left: calc(var(--space) * -1);
    margin-top: calc(var(--space) * -1);
    margin-bottom: calc(var(--space) / 2);
    overflow: hidden;
    border-radius: var(--radius) var(--radius) 0 0;
    
    img {
      width: 100%;
      max-width: 80%; 
      margin-left: 10%; 
      margin-top: 5%;
    }

    &:empty {
      display: none;
    }
  }

  &__content {
    h2:first-child {
      margin-top: 0;
    }

    p:first-of-type {
      font-size: 1.2em;
      color: var(--title-color);
    }

    img {
      //width: calc(100% + var(--space) * 2);
      //margin-left: calc(var(--space) * 1);
      width: 100%;
      display: block;
      max-width: none;
    }
  }
}

.post-comments {
  padding: calc(var(--space) / 2);
  
  &:empty {
    display: none;
  }
}

.post-author {
  margin-top: calc(var(--space) / 2);
}
</style>