<template>
     
  <div class="site">
  

    <div class="parent">
      <div class="name-about-container">
        <h1 class="name">JEREMY FIELDS</h1>
        <h6 id="about">
          Data Scientist at <a href="https://about.bgov.com/" target="_blank">@Bloomberg Government</a></br>
          Check me out on
          <a href="https://www.twitter.com/delafields" target="_blank">Twitter</a>,
          <a href="https://www.github.com/delafields" target="_blank">Github</a>
          or check my <a href="https://delafields.github.io/" target="_blank">Data Science Portfolio</a>
        </h6>
      </div>
    </div>

		<div class="page-links">
      <g-link to="/projects" class="page-link">PROJECTS</g-link>
      </br>
			<g-link to="/blog" class="page-link">BLOG</g-link>
			</br>
			<a href="mailto:jeremyfieldsmail@gmail.com" target="_blank" class="page-link">
        CONTACT
      </a>
		</div>
    

    <TinyFooter />
    

	</div> 

</template>

<page-query>
{
  projects: allPost {
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
        date (format: "D. MMMM YYYY")
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
import TinyFooter from '~/components/TinyFooter.vue'

export default {

  components: {
    TinyFooter
  },
  metaInfo: {
    title: ''
  }
}
</script>

<style scoped lang="sass">
@import "../assets/style/_myold.sass"

/* Layout */
.site
  @include grid-layout
  @include three-borders-in-a-good-neighborhood

.parent
  background-image: url("../assets/images/natural-paper.png"), url('../assets/images/background-stripes.svg')
  background-size: auto, cover
  grid-area: content

.name-about-container
  margin-left: 20px

.page-links
  position: fixed
  bottom: 60px
  right: 50px
  text-align: center

/* Typography */

// Font Family
.name, #about, .page-link
  @include news-cycle

// Sizing
.name, .page-link
  font-size: 30px

// Colors
.name
  color: black

#about, .page-link
  color: red

#about > a
  color: black

// Quirks
.name
  letter-spacing: 5px
  padding-top: 10px
  margin-bottom: 10px

#about
  font-size: 12px
  margin: none

.page-link
  @include shadow-transition
  &:hover
    @include shadow-to-left

.page-link, #about > a
  text-decoration: none
  &:visited, &:active
    text-shadow: none

// Media Queries
@media screen and (max-width: 800px)
  .site
    @include grid-layout-mobile
</style>