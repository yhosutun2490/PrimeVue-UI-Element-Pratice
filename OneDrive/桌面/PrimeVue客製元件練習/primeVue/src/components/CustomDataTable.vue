<script setup>
import DataTable from 'primevue/datatable';
import Column from 'primevue/column';
import{ref,onMounted} from 'vue'
import { ProductService } from '../data/product';
const products = ref(null)
onMounted(()=> {
  ProductService.getProductsMini().then((data) => 
  {
    products.value = data
    console.log("product data",data)
  
  }
  );
})
</script>
<template>
  <DataTable :value="products" showGridlines tableStyle="min-width: 50rem">
    <Column field="code" header="Code"></Column>
    <Column field="name" header="Name"></Column>
    <Column field="category" header="Category"></Column>
    <Column field="quantity" header="Quantity"></Column>
  </DataTable>
  
</template>

<style scoped>

</style>
