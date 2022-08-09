<template>
    <div id="nav">
        <router-link to="/" id="logo-url">
            <img id="logo" :src="logo" :alt="alt">
        </router-link>
        <router-link to="/">Home</router-link>
        <router-link to="/Requests">Pedidos</router-link>
    </div>
</template>

<script>
    export default{
        name: 'Navbar',
        props: ['logo', 'alt'],
    }
</script>

<style scoped>
    #nav{
        display: flex;
        flex-flow: row wrap;
        align-items: center;
        
        background-color: #111;
    }

    #nav #logo-url{
        margin: auto;
        margin-left: 1.5%;
    }

    #nav a{
        text-decoration: none;
        font-size: 16pt;
        color: #ffff;
        padding: 0.5%;
        margin-right: 3%;

        transition: 0.5s;
    }

    #nav a:hover{
        color: #ffc400;
    }

    #logo{
        width: 50px;
        height: 50px;
        margin: 5%;
    }
</style>