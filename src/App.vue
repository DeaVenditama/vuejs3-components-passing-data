<template>
    <Title title="Catatan Pengeluaran" />
    <FormPengeluaran @entri-pengeluaran="entriPengeluaran($event)" />
    <h2>Total Pengeluaran : {{ totalPengeluaran }}</h2>
    <h2 v-if="warning" class="warning">Pengeluaran Anda Terlalu Banyak</h2>
	<ListPengeluaran v-if="showList" :dataPengeluaran="dataPengeluaran" />
</template>

<script>
    import Title from "./components/Title.vue";
    import ListPengeluaran from "./components/ListPengeluaran.vue";
    import FormPengeluaran from "./components/FormPengeluaran.vue";
    import { ref, computed, watch } from 'vue';

    export default {
        name: "App",
        components: {
            Title,
            ListPengeluaran,
            FormPengeluaran,
        },
        setup(){
            const dataPengeluaran = ref([]);
            const warning = ref(false);

            function entriPengeluaran(event){
                dataPengeluaran.value.push(event);
            }

            const showList = computed( () => dataPengeluaran.value.length > 0 );
            const totalPengeluaran = computed(()=>dataPengeluaran.value.reduce(
                                                (accum, item) => accum + parseInt(item.nominal),
                                                0)
                                            );
            watch(totalPengeluaran, (newValue)=>{
                if (newValue > 100000) {
                    warning.value = true;
                } 
            });
            
            return{
                dataPengeluaran,
                warning,
                entriPengeluaran,
                showList,
                totalPengeluaran
            }
        },
    };
</script>

<style>
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
    }
</style>
