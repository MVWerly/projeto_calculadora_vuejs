<script setup>
    const props = defineProps(['historico', 'deleteHistorico']);
</script>

<template>
    <div class="row mt-5">
        <h2 class="text-center">Resultados</h2>
        <div class="col">
            <ul class="list-group">
                <li class="list-group-item d-flex align-items-center justify-content-between mt-2"
                    v-for="historico in props.historico">
                    <label>{{ historico.valorHistoricoUm }} {{ historico.operacaoHistorico }} {{
                        historico.valorHistoricoDois }}
                        = {{ historico.resultadoHistorico }}</label>
                    <button :id="historico.id" @click="props.deleteHistorico" type="reset"
                        class="btn btn-danger ms-3">X</button>
                </li>
            </ul>
        </div>
    </div>
</template>