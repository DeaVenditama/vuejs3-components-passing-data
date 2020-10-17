<template>
  <table>
    <tr>
      <th>Pengeluaran</th>
      <th>Keterangan</th>
    </tr>
    <tr v-for=" (pengeluaran,index) in dataPengeluaran" :key="index">
      <td>{{ pengeluaran.nominal }}</td>
      <td>{{ pengeluaran.keterangan }}</td>
    </tr>
  </table>
</template>

<script>
export default {
  props:{
    dataPengeluaran : Array
  }
}
</script>

<style scoped>
  table {
    border-collapse: collapse;
    width: 100%
  }

  table, th, td{
    border: 1px solid black;
  }

  th {
    background-color: #8e44ad;
    color: white;
  }

  th, td{
    padding: 5px;
  }

  td {
    text-align: center;
    color:#8e44ad; 
  }

  tr:hover td{
    background-color: #f5f5f5;
    cursor: pointer;
  }
</style>