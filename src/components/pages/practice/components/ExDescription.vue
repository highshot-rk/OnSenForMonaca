<template>
    <p>
        <slot></slot>
    </p>
</template>

<script>
export default {
    name: 'ex-description'
}
</script>

<style scoped>
    p {
        font-weight: bold;
        padding: 2px;
        font-size: 0.8rem;
        text-align: left;
    }
</style>