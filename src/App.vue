<template>
  <div id="app" class="small-container">
    <h1>Master List Table</h1>

    <master-table />
    <drafted-table />
  </div>
</template>

<script>
import MasterTable from '@/components/MasterTable.vue'
import DraftedTable from '@/components/DraftedTable.vue'
import MasterTableTest from '@/json/MasterTableTest.json'

export default {
  name: 'App',
  data(){
    return{
      masterData: MasterTableTest
    }
  },
  components: {
    MasterTable,
    DraftedTable,
  },
}
</script>

<style>

button {
  background: #009435;
  border: 1px solid #009435;
}

.small-container {
  max-width: 680px;
}
</style>
