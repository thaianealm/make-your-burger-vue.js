<template>
    <div class="main-banner">
        <h1>Monte <br/>Seu <br/>Hambúrguer</h1>
    </div>
</template>

<script>
    export default{
        name: 'Banner',
    }
</script>

<style scoped>
    .main-banner{
        display: flex;
        justify-content: flex-start;
        height: 80vh;
        background-image: url('/public/img/burger-banner.jpg');
        background-position: 0 -380px;
        background-size: cover;
        background-repeat: no-repeat;
    }

    .main-banner h1{
        height: 70px;
        width: 50%;
        color: #fff;
        font-size: 60pt;
        text-align: left;
        margin-left: 5%;
    }
</style>