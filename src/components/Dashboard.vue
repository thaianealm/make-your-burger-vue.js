<template>
    <div class="burger-table">
        <div>
            <div class="burger-table-heading">
                <div class="order-id">#:</div>
                <div>Cliente:</div>
                <div>Pão:</div>
                <div>Carne:</div>
                <div>Opcionais:</div>
                <div>Ações</div>
            </div>
        </div>
         <div class="burger-table-rows">
            <div class="burger-table-row" v-for="burger in burgers" :key="burger.id">
                <div class="order-number">{{ burger.id }}</div>
                <div>{{ burger.name }}</div>
                <div>{{ burger.bread }}</div>
                <div>{{ burger.meat }}</div>

                <div>
                    <ul>
                        <li v-for="(opcional, index) in burger.opcionais" :key="index">{{ opcional }}</li>
                    </ul>
                </div>
                
                <div>
                    <select name="status" class="status">
                        <option value="">Selecione</option>
                        <option v-for="s in status" :key="s.id" value="s.tipo" :selected="burger.status == s.tipo">{{ s.tipo }}</option>
                    </select>
                    <button class="delete-btn" @click="deleteBurger(burger.id)">Cancelar</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default{
    name: 'Dashboard',
    data(){
       return{
        burgers: null,
        burgers_id: null,
        status: []
       }
    },
    methods:{
        async getRequests(){

            const req = await fetch('http://localhost:3000/burgers')
            const data = await req.json()
            this.burgers = data
        
            // Redeem order status
            this.getStatus()

        },
        async getStatus() {

            const req = await fetch('http://localhost:3000/status');
            const data = await req.json();
            this.status = data;
      },
        async deleteBurger(id) {
            const req = await fetch(`http://localhost:3000/burgers/${id}`,{
              method: 'DELETE'
            });
            const res = await req.json();

            this.getRequests();
      }
    },
    mounted(){
        this.getRequests();
    }
}
</script>

<style scoped>
 .burger-table {
    max-width: 79rem;
    margin: 0 auto;
  }
  .burger-table-heading,
  .burger-table-rows,
  .burger-table-row {
    display: flex;
    flex-wrap: wrap;
  }
  .burger-table-heading {
    padding: 12px;
    border-bottom: 3px solid #555555;

    font-weight: 500;
    font-size: 16pt;
  }
  .burger-table-row {
    width: 100%;
    padding: 24px;
    border-bottom: 1px solid #CCC;

    font-size: 14pt;
  }
  .burger-table-heading div,
  .burger-table-row div {
    width: 19%;
  }
  .burger-table-heading .order-id,
  .burger-table-row .order-number {
    width: 5%;
  }
  select {
    padding: 10px 5px;
    margin-right: 12px;
    border-radius: 6px;
    font-size: 12pt;
  }
  .delete-btn {
    background-color: #ff0000;
    color:#ffffff;
    border: none;
    border-radius: 6px;
    padding: 12px;
    font-size: 12pt;
    margin: 0 auto;
    cursor: pointer;
    transition: .5s;
  }
  
  .delete-btn:hover {
    background-color: #dd0000;
  }
</style>