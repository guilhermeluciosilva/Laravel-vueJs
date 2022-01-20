 <template>
 
    <DashBoardComponent>

      <div slot="slot-pages" class="content-pages">
        <header class="title_pages">
          <p>Produtos</p>
        </header>
      </div>

    </DashBoardComponent>
     
 </template>

 <script>
     
import DashBoardComponent from '../Dashboard/DashboardComponent.vue';

export default {
  name: 'ProductsComponent',

  components: {
      DashBoardComponent,
  }

 }
 </script>

<style lang="scss" src="./style.scss" scoped />
 