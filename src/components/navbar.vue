<template>
    <nav class="main-nav">
        <router-link :to="{name:'home'}">Anasayfa</router-link>
        <router-link :to="{name:'addproject'}">Plan Ekle</router-link>
    </nav>
</template>
<script>
export default{

}
</script>
<style>
.main-nav{
    text-align: center;
    margin: 40px auto;
}
.main-nav a{
    display: inline-block;
    text-decoration: none;
    margin: 0 10px;
    color: rgb(49, 48, 48);
    font-size: 18px;
}
a.router-link-active{
    border-bottom: 2px solid rgb(22, 162, 157);
    padding-bottom: 5px;
    color:rgb(22, 162, 157);
}
</style>