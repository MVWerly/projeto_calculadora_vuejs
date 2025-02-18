<script setup>
    const props = defineProps(['valorUm', 'valorDois', 'operacao', 'calcular'])
</script>

<template>
    <div class="row justify-content-center">
        <div class="screen rounded-3 mt-5">
            <span>{{ props.valorUm }} {{ props.operacao }} {{ props.valorDois }}</span>
            <h2>{{ props.calcular }}</h2>
        </div>
    </div>
</template>

<style scoped>
.screen {
    position: relative;
    width: 300px;
    height: 95px;
    background-color: rgb(106, 126, 106);
    overflow: hidden;
}

.screen span {
    position: absolute;
    top: 10px;
    right: 10px;
}

.screen h2 {
    position: absolute;
    font-weight: bold;
    bottom: 10px;
    right: 10px;
}
</style>