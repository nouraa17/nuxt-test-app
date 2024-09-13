<template>
  <div>
    <h1>About Dad jokes</h1>
    <p>This is an app to display corny dad jokes</p>
  </div>
</template>

<script>
export default {
  name: "about",
  head(){
    return{
      title:'About the app',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Best place for corny dad jokes'
        }
      ]
    }
  }
}
</script>


<style scoped>

</style>
