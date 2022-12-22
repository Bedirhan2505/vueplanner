<template>
  <div class="home">
    <filternav @filterchange="current = $event" :current="current"/>
    <div v-if="projects.length">
      <div v-for="project in filtrele" :keys="project.id">
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
import SingleProject from '../components/singleproject.vue';
import filternav from '../components/filternav.vue'
export default {
  name: 'Home',
  components: {SingleProject,filternav},
  data(){
    return{
      projects:[],
      current:"all"
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
computed:{
  filtrele(){
   if( this.current == "complated"){
      return this.projects.filter((project) => project.complete)
   }
   if( this.current == "ongoing"){
      return this.projects.filter((project) => !project.complete)
   }
   return this.projects;
  },
}
}
</script>
