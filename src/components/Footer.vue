<template>
    <div id="footer">
        <p>Monte Seu Hambúrguer &copy; 2022</p>
        <p>Desenvolvido por <a href="#">Thaiane</a></p>
    </div>
</template>

<script>
    export default{
        name: 'Footer',
    }
</script>

<style scoped>
    #footer {
        height: 20vh;
        display: flex;
        align-items: center;
        justify-content: center;
        bottom: 0;
        width: 100%;
        text-align: center;
        color: #fff;
        background-color: #111;
    }

    p{
        margin-left: 1%;
    }

    p a{
        color: #f1f1f1;
    }
</style>