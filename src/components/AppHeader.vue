<script>

export default {
    name: "AppHeader",
    props: {
        message: String,
    },
    methods: {},
};
</script>

<template>
    <header class="d-flex justify-content-start align-items-center ps-3 pe-3">
        <img src="/logo.png" />
        <h1 class="text-center text-light">{{ message }}</h1>
    </header>
</template>

<style lang="scss" scoped>
@use '../styles/partials/variables' as *;

header {
    height: 70px;
    background-color: $bg-color;
    line-height: 70px;
    border-bottom: 1px solid rgba(28, 28, 28, .6);

    img {
        height: 50px;
        margin: 0 10px;
    }

    h1 {
        padding: 0 10px;
    }
}
</style>