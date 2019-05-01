<template>
   <div class="post-meta">
      Posted {{ project.date }}.
      <template v-if="project.timeToRead">
        <strong>{{ project.timeToRead }} min read.</strong>
      </template>
    </div>
</template>

<script>
export default {
  props: ['project']
}
</script>

<style lang="scss">
.post-meta {
  font-size: .8em;
  opacity: .8;
  padding-top: .2em;
}
</style>