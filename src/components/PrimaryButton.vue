<template>
    <button type="button" class="btn btn-blue w-100">
        <slot></slot>
    </button>
</template>
<script>
export default {
    name: "PrimaryButton"
}
</script>
<style scoped>
.w-100 {
    display: flex;
    justify-content: center;
    width: 100%;
}
</style>