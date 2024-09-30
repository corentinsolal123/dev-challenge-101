<template>
    <div>
        <h1>{{ message }}</h1>
    </div>
</template>

<script>
export default {
    data() {
        return {
            message: process.env.VUE_APP_ENV_MODE || "Mode non défini",
        }
    },
}
</script>

<style>
body {
    background-color: black;
    color: white;
}
</style>
