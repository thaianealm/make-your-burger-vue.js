<template>
    <footer id="footer">
        <p>Monte Seu Hambúrguer &copy; 2022</p>
        <p id="dev">Desenvolvido por <a href="#">Thaiane</a></p>
    </footer>
</template>

<script>
    export default{
        name: 'Footer',
    }
</script>

<style scoped>
    #footer{      
        display: flex;
        flex-flow: column wrap;
        align-content: center;
        justify-content: center;
        position: absolute;
        bottom:0;
        width:100%;
        height: 20vh;
        margin: auto auto;
        padding: 10px 5px;


        text-align: center;
        color: #fff;
        background-color: #111;
    }

    #dev{
        margin-top: 1.5%;
    }

    a{
        color: #f1f1f1;
    }
</style>