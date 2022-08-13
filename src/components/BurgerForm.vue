<template>
    <div>
        <form id="buger-form">
            <div class="input-container">
                <label for="name">Nome:</label>
                <input type="text" name="name" v-model="name" placeholder="Digite o seu nome">
            </div>

            <div class="input-container">
                <label for="bread">Escolha um tipo de pão:</label>
                <select name="bread" id="bread" v-model="bread">
                    <option value="">Selecione o pão</option>
                </select>
            </div>

            <div class="input-container">
                <label for="meat">Escolha um tipo de carne:</label>
                <select name="meat" id="meat" v-model="meat">
                    <option value="">Selecione a carne</option>
                </select>
            </div>

            <div class="input-container add-container">
                <label for="add" class="add-title">Complementos:</label>
                <div class="checkbox-container">
                    <input type="checkbox" name="add" class="add">
                    <span>Bacon</span>
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
    }
</script>

<style scoped>
    #buger-form{
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