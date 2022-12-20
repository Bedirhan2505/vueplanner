<template>
    <div class="project">
        <div class="actions">
            <h3 @click="showDetails = !showDetails">{{project.title}}</h3>
        </div>
        <div class="details" v-if="showDetails">
            <h3>{{project.details}}</h3>
        </div>
    </div>
</template>

<script>
export default{
    props: ['project'],
    data(){
        return{
            showDetails:false,
        }
    }
}
</script>

<style>
.project{
    margin: 20px auto;
    background: #fff;
    padding: 10px 20px;
    border-radius: 5px;
    box-shadow: 1px 2px 3px rgba(0,0,0,05);
    border-left: 4px #e90074;
    cursor: pointer;
}
</style>