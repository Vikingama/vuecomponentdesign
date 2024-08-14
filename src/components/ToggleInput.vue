<template>
    <span
        class="toggle flex-no-shrink"
        role="checkbox"
        tabindex="0"
        :aria-checked="toggled"
        @click="handleToggle"
        @keydown.space.prevent="handleToggle"
    ></span>
</template>
<script>
export default {
    name: "ToggleInput",
    // 重新设置 v-model 默认绑定的值和事件
    model: {
        prop: "toggled",
        event: "toggle"
    },
    props: ["toggled"], // value => toggled
    methods: {
        handleToggle () {
            const reverseToggled = !this.toggled
            // 触发 v-model 绑定的事件，更新绑定的值
            this.$emit("toggle", reverseToggled)
        }
    }
}
</script>