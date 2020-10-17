<template>
  <form class="form-pengeluaran" @submit.prevent="catat" >
    <div>
      <label>Pengeluaran</label>
      <input v-model="pengeluaran" type="number" id="pengeluaran">
    </div>
    <div>
      <label>Keterangan</label>
      <input v-model="keterangan" type="text" id="keterangan">
    </div>
    <div>
      <button>Catat!</button>
    </div>
  </form>   
</template>

<script>
export default {
  data(){
    return{
      pengeluaran: null,
      keterangan: null,
    }
  },
  methods:{
    catat(){
      this.$emit('entri-pengeluaran', {
        nominal : this.pengeluaran,
        keterangan: this.keterangan,
      });
      this.pengeluaran = null;
      this.keterangan = null;
      document.getElementById("pengeluaran").focus();
    }
  }
}
</script>

<style scoped>
  .form-pengeluaran{
    padding: 20px;
    display: flex;
    flex-flow: row wrap;
    align-items: center;
    justify-content: center;
  }

  .form-pengeluaran label{
    margin: 5px 10px 5px 0;
  }

  .form-pengeluaran input{
    vertical-align : middle;
    margin : 5px 10px 5px 0;
    padding : 10px;
    background-color: #fff;
    border: 1px solid #ddd;
  }

  .form-pengeluaran button:hover{
    background-color: #a76ec0;
  } 

  .form-pengeluaran button {
    padding : 10px 20px;
    background-color: #a76ec0;
    border: 1px solid #ddd;
    color: white;
    cursor: pointer;
  }
</style>