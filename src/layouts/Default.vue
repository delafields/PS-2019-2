<template>
  <div id="app">

    <header class="header">
      <div class="header__left">
        &larr; <g-link 
                id="back-link"
                :to="backLinkPath">
                {{ backLinkName }}
                </g-link> 
      </div>

      <div class="header__center">
        <h1 id="title">
          {{ titleName }}
        </h1>
      </div>
      
      <div class="header__right">        
        <ToggleTheme />
      </div>
    </header>

    <main class="main">
      <slot/>
      <TinyFooter />
    </main>

    
  </div>
</template>

<script>
import ToggleTheme from '~/components/ToggleTheme.vue'
import TinyFooter from '~/components/TinyFooter.vue'

export default {
  props: {
    titleName: String,
    backLinkPath: String,
    backLinkName: String
  },
  components: {
    ToggleTheme,
    TinyFooter
  }
}
</script>

<style lang="scss">
#app {
  border-top: 20px solid white; 
  border-right: 20px solid white; 
  border-left: 20px solid white; 
}
  

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  min-height: var(--header-height);
  padding: 0 calc(var(--space) / 2);
  top:0;
  z-index: 10;

  &__left,
  &__center,
  &__right {
    display: flex;
    align-items: center;
  }

  &__center > #title {
    font-size: 1.602em;
    font-family:'Monoton', sans-serif; 
    font-weight: 300; 
    margin-bottom: 0;
  }

  &__left {
    &:hover {
      text-shadow: 4px 3px 3px rgba(255, 23, 68, 0.60), 1px 1px 3px rgba(255, 255, 255, 0.4);
      transition: text-shadow .2s ease-in-out;
    }
    #back-link {
      text-decoration: none; 
      margin-left: 5px;
    }
  }

  @media screen and (min-width: 1300px) {
    //Make header sticky for large screens
    position: sticky;
    width: 100%;
  }
}

.main {
  margin: 0 auto;
  padding: 1.5vw 15px 0;
}

</style>
