<template>
  <nav class="filter-nav">
    <button @click="updatefilter('all')" :class="{active: current === 'all'} ">All</button>
    <button @click="updatefilter('complated')" :class="{active: current ==='complated'} ">Completed</button>
    <button @click="updatefilter('ongoing')" :class="{active: current === 'ongoing'} ">OnGoing</button>
  </nav>
</template>

<script>
export default {
    props:["current"],
    methods:{
        updatefilter(by){
            this.$emit("filterchange", by)
        }
    }

}
</script>

<style>
.filter-nav button{
  background: none;
  border: none;
  color:#bbb;
  outline: none;
  font-size: 12px;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
  cursor: pointer;
  margin: 0px;
  padding: 10px;

}
.filter-nav button:active{
  color: #555;
}
.filter-nav button:hover{
  color: rgb(49, 222, 211);
}
</style>