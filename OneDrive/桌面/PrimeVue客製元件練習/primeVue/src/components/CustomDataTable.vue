<script setup>
import DataTable from 'primevue/datatable';
import Column from 'primevue/column'; 
import "primevue/resources/themes/lara-light-blue/theme.css";
import{ref,onMounted} from 'vue'
import { ProductService } from '../data/product';
const products = ref(null)
onMounted(()=> {
  ProductService.getProductsWithOrders().then((data) => 
  {
    products.value = data
    console.log("product data",data)
  
  }
  );
})
</script>
<template>
  <DataTable 
  :value="products" 
  :pt="{
     wrapper: { 
      class: 'table-wrapper', 
      },
     thead: {
      class: 'table-head',
     },
     headerRow: {
      class: 'table-head-row'
     },
     virtualScroller: {
      class: 'table-scrollbar'
     }
    }"
  showGridlines
  scrollable 
  scrollHeight="400px" 
  tableStyle="min-width: 50rem">
    <Column field="code" header="Code"></Column>
    <Column field="name" header="Name"></Column>
    <Column field="category" header="Category"></Column>
    <Column field="quantity" header="Quantity"></Column>
  </DataTable>
  
</template>

<style scoped>
:deep(.table-wrapper) {
  border: 1px solid green;
  border-radius: 15px;
}
:deep(.table-head >tr>th) {
  background: white;
}
:deep(.table-head-row th) {
  border-width: 1px 0 1px 0;
} 
:deep(.table-scrollbar) {
  width: 5px;
}

</style>
