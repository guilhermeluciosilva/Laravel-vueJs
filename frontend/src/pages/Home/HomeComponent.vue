 <template>
 
    <DashBoardComponent>

      <div slot="slot-pages" class="content-pages">
        <header class="title_pages">
           <p>Inicio</p>
        </header>
      
      <div>
        <div class="row">
          <div class="col-12 col-md-3">
            <CardsComponent :type="'Clientes'" :percentagem="'7%'" :icon="'fa-users'" :qtd="clients.length"/>
          </div>

          <div class="col-12 col-md-3">
            <CardsComponent :type="'Produtos'" :percentagem="'12%'" :icon="'fa-box'" :qtd="products.length"/>
          </div>
          
          <div class="col-12 col-md-3">
            <CardsComponent :type="'Serviços'" :percentagem="'3%'" :icon="'fa-store'" :qtd="products.length"/>
          </div>

          <div class="col-12 col-md-3"> 
            <CardsComponent :type="'Relátorios'" :percentagem="'25%'" :icon="'fa-chart-bar'" :qtd="products.length"/>
          </div>

          
        </div>

        <div class=" mt-5">
          <div class="row">
            <div class="col-12 col-md-6">
              <ListsComponent :data="clients" description="Clientes" :columns="['Nome', 'E-mail']"/>
            </div>

            <div class="col-12 col-md-6">
              <ListsComponent :data="products" description="Produtos" :columns="['Nome', 'Valor']"/>
            </div>
          </div>
        </div>
      </div>
    </div>

    </DashBoardComponent>
     
 </template>

 <script>
     
import DashBoardComponent from '../Dashboard/DashboardComponent.vue';
import CardsComponent from '../../components/CardsComponent.vue';
import ListsComponent from '../../components/ListsComponent.vue';
const axios = require('axios');

export default {
  name: 'HomeComponent',
  data() {
    return{
      clients: [],
      products: [],
    }
  },

  mounted() {
    this.getUsers();
  },

  methods: {
    async getUsers(){
      

       try{
          let response = await axios.get('/');
          
            this.clients = response.data.clients;
            this.products = response.data.products;
          

       }catch(error){
            console.error("Aconteceu um erro: "+error.response.status);
       }



    }
  },
  components: {
      DashBoardComponent,
      CardsComponent,
      ListsComponent,
  }

 }
 </script>

 <style lang="scss" src="./style.scss" scoped />
 