<template>
    <div>
        <p>
            <slot />
        </p>
        <div class="bottom-line" />
    </div>
</template>

<script>
export default {
    name: 'ex-title'
}
</script>

<style scoped>
    p {
        color: #0089FF;
        font-weight: 900;
        font-size: 1.4rem;
        text-align: left;
    }
    div.bottom-line {
        width: 15%;
        margin-left: 0px;
        border: 1px solid #0089FF;
    }
</style>