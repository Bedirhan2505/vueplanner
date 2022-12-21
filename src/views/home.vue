<template>
  <div class="home">
    <div v-if="projects.length">
      <div v-for="project in projects" :keys="project.id">
        <singleProject 
        :project="project" 
        @delete="handledelete"
        @complete="handlecompleted"
        ></singleProject>
      </div>
    </div>
  </div>
</template>

<script>
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

  },
methods: {
  handledelete(id){
    this.projects = this.projects.filter((project) => project.id !== id)
  },
  handlecompleted(id){
    let p = this.projects.find(project  => project.id === id);
    p.complete= !p.complete;
  }
},
}
</script>
