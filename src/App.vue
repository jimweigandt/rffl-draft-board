<template>
  <div id="app" class="small-container">
    <h1>Master List Table</h1>

    <master-table />
  </div>
</template>

<script>
import MasterTable from '@/components/MasterTable.vue'

export default {
  name: 'App',
  components: {
    MasterTable,
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
