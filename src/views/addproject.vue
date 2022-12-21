<template>
  <form @submit.prevent="handleSubmit">
    <h5>Plan oluşturmak artık çok kolay. Hemen detayları gir ve bir plan oluştur....</h5>
    <label for="title"> Başlık : </label>
    <input name="title" type="text" required v-model="title"><br>
    <label for="details"> Detaylar :</label>
    <textarea name="details" v-model="details" required></textarea><br>
    <button>Ekle</button>
  </form>
</template>
<script>
  export default {
    data() {
      return{
        title:"",
        details:""
      }
    },
    methods : {
      handleSubmit(){
        let d = {
          title: this.title,
          details:this.details,
          complete:false  
        };
        fetch('http://localhost:3000/projects',{
          method: 'POST',
          headers: {"Content-Type" : "application/json"},
          body: JSON.stringify(d)
        })
        .then(()=>this.$router.push("/"))
        .catch(err=>console.log(err));
      }
    }
  }
</script>
<style>
form{
  background: rgb(20, 211, 205);
  margin: 30px auto;
  width: 300px;
  height: 400px;
  border-radius: 20px;
  padding: 5px 20px;
}
h5{
  text-align: center;
  font-size: 14px;
  font-weight: bold;
}
label{
  margin:15px 10px 10px 5px;
  display: block;
  text-transform: uppercase;
  font-size: 14px;
  font-weight: bold;
  color: aquamarine;
  letter-spacing: 1px;
}
input{
  padding: 10px;
  border: 0;
  border-bottom: 2px solid #ddd;
  width: 100%;
  box-sizing: border-box;
}
textarea{
  padding: 10px;
  border: 2px solid #ddd;
  width: 100%;
  box-sizing: border-box;
  height: 150px;
}
button{
  margin: 20px 0;
  font-size: 16px;
  border-radius: 10px;
  border: 0;
  border-bottom:2px solid #ddd ;
  width: 100px;
  height: 30px;
  font-family:Verdana, Geneva, Tahoma, sans-serif;
  cursor: pointer;
}
</style>