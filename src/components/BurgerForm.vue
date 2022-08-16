<template>
    <div>
        <form id="burger-form" @submit.prevent="createBurger">
            <div class="input-container">
                <label for="name">Nome:</label>
                <input type="text" name="name" v-model="name" placeholder="Digite o seu nome">
            </div>

            <div class="input-container">
                <label for="bread">Escolha um tipo de pão:</label>
                <select name="bread" id="bread" v-model="bread">
                    <option value="">Selecione o pão</option>
                    <option v-for="bread in paes" :key="bread.id" :value="bread.tipo">{{ bread.tipo }}</option>
                </select>
            </div>

            <div class="input-container">
                <label for="meat">Escolha um tipo de carne:</label>
                <select name="meat" id="meat" v-model="meat">
                    <option value="">Selecione a carne</option>
                    <option v-for="meat in carnes" :key="meat.id" :value="meat.tipo">{{ meat.tipo }}</option>
                </select>
            </div>

            <div class="input-container add-container">
                <label for="opcionais" class="add-title">Complementos:</label>
                <div class="checkbox-container" v-for="opcional in opcionaisdata" :key="opcional.id">
                    <input class="add" type="checkbox" name="opcionais" v-model="opcionais" :value="opcional.tipo">
                    <span>{{ opcional.tipo }}</span>
                </div>
            </div>

            <div class="input-container">
                <input class="submit-btn" type="submit" value="Criar meu Hambúrguer">
            </div>
        </form>
    </div>
</template>

<script>
    export default{
        name: 'BurgerForm',
        data(){
            return{
                paes: null,
                carnes: null,
                opcionaisdata: null,
                name: null,
                bread: null,
                meat: null,
                opcionais: [],
                msg: null
            }
        },
        methods:{
            async getIngredients(){

                const req = await fetch('http://localhost:3000/ingredientes');
                const data = await req.json();

                this.paes = data.paes;
                this.carnes = data.carnes;
                this.opcionaisdata = data.opcionais;
            },
            async createBurger(){
                const data = {
                    name: this.name,
                    bread: this.bread,
                    meat: this.meat,
                    //o elemento opcionais precisa ir como array, então precisamos criar um array
                    opcionais: Array.from(this.opcionais), 
                    status: 'Solicitado',
                }
                const dataJson = JSON.stringify(data);

                const req = await fetch('http://localhost:3000/burgers',{
                    method: 'POST',
                    headers: { "Content-Type" : "application/json" },
                    body: dataJson,
                });

                const res = await req.json();

                //clear inputs
                this.name = '';
                this.bread = '';
                this.meat = '';
                this.opcionais = '';
            }
        },
        mounted(){
            this.getIngredients()
        }
    }
</script>

<style scoped>
    #burger-form{
        margin: 2% auto;
        max-width: 25rem;
    }

    .input-container{
        display: flex;
        flex-flow: column wrap;
        margin-bottom: 5%;
    }

    .input-container label{
        font-size: 17pt;
        margin-bottom: 1%;
    }

    .input-container input{
        padding: 0.938rem;
        font-size: 15pt;
    }

    select{
        padding: 0.600rem;
    }

    select option{
        font-size: 13pt;
    }

    .add-container{
        flex-flow: row wrap;
    }

    .input-container .checkbox-container .add{
        width: 1.5rem;
        height: 1.5rem;
    }

    .add-title{
        width: 100%;
    }

    .checkbox-container{
        display: flex;
        align-items: flex-start;
        width: 50%;
        margin-top: 5%;
        margin-bottom: 5%;
    }

    .checkbox-container span,
    .checkbox-container input{
        width: auto;
    }

    .checkbox-container span{
        margin-left: 5%;
        font-size: 16pt;  
        font-weight: 500;
    }

    .input-container .submit-btn{
        -webkit-border-radius: 20px;
        -moz-border-radius: 20px;
        border-radius: 20px;
        color: #FFFFFF;
        font-size: 18pt;
        padding: 16px;
        background-color: #ee8700;
        text-decoration: none;
        cursor: pointer;
        text-align: center;
        border: none;
        width: 20rem;
        margin: 4% auto;
        transition: all 0.4s ease-in-out;
    }

    .submit-btn:hover{
        background: #FFB300;
        border: none;
        -webkit-border-radius: 20px;
        -moz-border-radius: 20px;
        border-radius: 20px;
        text-decoration: none;
    }

    .submit-btn:active{
        cursor:pointer;
        position:relative;
        top:2px;
    }
</style>