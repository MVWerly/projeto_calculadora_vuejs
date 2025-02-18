<script setup>
    const props = defineProps(['enviarHistorico', 'limpar', 'getValorUm', 'getValorDois', 'getOperacao'])
</script>

<template>
    <div class="row mt-5">
        <form @submit.prevent="props.enviarHistorico" @reset="props.limpar">
            <div class="row">
                <div class="col input-group">
                    <input @input="props.getValorUm"
                        class="rounded-3 form-control" type="number" placeholder="Digite um valor:" required>
                </div>
                <div class="col">
                    <select @change="props.getOperacao"
                        class="rounded-3 form-control text-center">
                        <option selected>+</option>
                        <option>-</option>
                        <option>/</option>
                        <option>*</option>
                    </select>
                </div>
                <div class="col input-group">
                    <input @input="props.getValorDois"
                        class="rounded-3 form-control" type="number" placeholder="Digite um valor:" required>
                </div>
            </div>
            <div class="row mt-5">
                <div class="col-auto">
                    <button type="reset" class="btn btn-warning p-2">Limpar</button>
                </div>
                <div class="col-auto">
                    <button type="submit" class="btn btn-success p-2">Enviar</button>
                </div>
            </div>
        </form>
    </div>
</template>

<style scoped>
input,
select {
    font-size: 20px;
}

input[type="number"]::-webkit-outer-spin-button,
input[type="number"]::-webkit-inner-spin-button {
    -webkit-appearance: none;
    margin: 0;
}
</style>