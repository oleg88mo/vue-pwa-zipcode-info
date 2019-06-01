<template>
    <ion-button color="light" expand="block" v-if="zipData" @click="$emit('clear-data')">Clear</ion-button>
</template>

<script>
    export default {
        name: "ClearData",
        props: ['zipData']
    }
</script>