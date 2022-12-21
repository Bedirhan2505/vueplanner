<template>
    <div class="project" :class="{ complete : project.complete}">
        <div class="actions">
            <h3 @click="showDetails = !showDetails">{{project.title}}</h3>
        <div class="icons">
            <span class="material-icons" @click="editproject">edit</span>
            <span class="material-icons" @click="deleteproject">delete</span>
            <span class="material-icons done" @click="completedproject">done</span>
        </div>
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
            uri: 'http://localhost:3000/projects/' + this.project.id,
        }
    },
    methods:{
        deleteproject(){
            fetch(this.uri,{method:"DELETE"})
            .then(()=>this.$emit("delete", this.project.id))
            .catch((err) => console.log(err.message));
        },
        completedproject(){
            fetch(this.uri,{
                method: "PATCH",
                headers: {"Content-Type" : "application/json"},
                body: JSON.stringify({complete : !this.project.complete}) 
        
        })
            .then(()=>this.$emit("complete", this.project.id))
            .catch((err) => console.log(err));
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
    border-left: 4px solid #e91700;
    cursor: pointer;
}
.actions{
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.material-icons{
    font-size: 24px;
    margin-left: 10px;
    color: #bbb;
    cursor: pointer;

}
.material-icons:hover{
    color: rgb(106, 106, 106);
}
.project.complete {
    border-left: 4px solid #008f79;
}
.project.complete .done{
    color:#008f79;
}
</style>