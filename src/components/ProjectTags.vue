<template>
   <div class="post-tags">
   		<g-link 
			 	class="post-tags__link" 
				v-for="tag in project.tags" 
				:key="tag.id" 
				:to="tag.path"
			>
   			<span>#</span>{{ tag.title }}
   		</g-link>
    </div>
</template>

<script>
export default {
  props: ['project']
}
</script>

<style lang="scss">
.post-tags {
  //margin: 1em 0 0;

  &__link {
  	margin-right: .5em;
  	font-size: .8em;
		//color: currentColor;
  	text-decoration: none;
  	//background-color: var(--bg-color);
  	//color: currentColor!important; //Todo: remove important;
  	padding: .5em;
  	border-radius: var(--radius);
  }
}
</style>