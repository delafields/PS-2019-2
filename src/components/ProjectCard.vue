<template>
  <div class="post-card content-box2" :class="{'post-card--has-poster' : project.poster}">
    <div class="post-card__header">
      <g-image alt="Cover image" v-if="project.coverImage" class="post-card__image" :src="project.coverImage" style="max-width:90%;"/>
    </div>
    <div class="post-card__content">
      <h2 class="post-card__title" v-html="project.title" />
      <p class="post-card__description" v-html="project.description" />
      
      <div class="post-card__footer">
        <ProjectMeta class="post-card__meta" :project="project" />
        <ProjectTags class="post-card__tags" :project="project" />
      </div>

      <g-link class="post-card__link" :to="project.path">Link</g-link>
    </div>
  </div>
</template>

<script>
import ProjectMeta from '~/components/ProjectMeta'
import ProjectTags from '~/components/ProjectTags'

export default {
  components: {
    ProjectMeta,
    ProjectTags
  },
  props: ['project'],
}
</script>

<style lang="scss" scoped>
.post-card {
  margin-bottom: var(--space);
  position: relative;

  &__header {
    //margin-left: calc(var(--space) * -1);
    margin-right: calc(var(--space) * -1);
    margin-bottom: calc(var(--space) / 2);
    //margin-top: calc(var(--space) * -1);
    overflow: hidden;
    border-radius: var(--radius) var(--radius) 0 0;

    &:empty {
      display: none;
    }
  }

  &__image {
    max-width: 100%;
  }

  &__content {
    //align-items: stretch;
  }

  &__title {
    margin-top: 0;
    text-align: center;
    text-transform: uppercase;
  }

  &__description {
    text-align: center;
    font-size: 0.75em;
  }

  &:hover {
    transform: translateY(-5px);
    box-shadow: 1px 10px 30px 0 rgba(0,0,0,.1);
  }

  &__footer {
    flex-direction: column;
    align-items: center;
    border-top: 1px dotted currentColor; 
    padding-top: 10px;
    margin-top: auto;
  }

  &__tags {
    z-index: 1;
    position: relative;
    margin-left: .5em;
  }

  &__link {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    opacity: 0.0;
    overflow: hidden;
    text-indent: -9999px;
    z-index: 0;
  }
}
</style>