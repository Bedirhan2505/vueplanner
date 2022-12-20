<template>
  <div class="home">
    <div v-if="projects.length">
      <div v-for="project in projects" :keys="project.id">
        <singleProject :project="project"></singleProject>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import SingleProject from '../components/singleproject.vue'
export default {
  name: 'Home',
  components: {SingleProject},
  data(){
    return{
      projects:[]
    }
  },
  mounted(){
    fetch('http://localhost:3000/projects')
    .then(res => res.json())
    .then(data =>this.projects = data)
    .catch(err => console.log(err.message))

  }

}
</script>
