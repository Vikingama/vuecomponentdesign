<template>
    <div class="accordion-item">
        <div @click="toggle" role="button" class="accordion-item-header">
            <slot name="header"></slot>
            <svg
                class="icon"
                viewBox="0 0 20 20"
                xmlns="http://www.w3.org/2000/svg"
                :class="{ 'rotate-90': active }"
            >
                <path
                    d="M12.95 10.707l.707-.707L8 4.343 6.586 5.757 10.828 10l-4.242 4.243L8 15.657l4.95-4.95z"
                />
            </svg>
        </div>
        <div class="accordion-item-body" v-show="active">
            <slot name="content"></slot>
        </div>
    </div>
</template>
<script>
export default {
    name: "AccordionItem",
    inject: ["accordionListState"],
    props: ["itemId"],
    computed: {
        active () {
            return this.accordionListState.activeItem === this.itemId
        }
    },
    methods: {
        toggle () {
            this.accordionListState.activeItem = this.active ? null : this.itemId;
        }
    }
}
</script>
<style scoped>
.rotate-90 {
    transform: rotateZ(90deg);
    transition: all 0.3s;
}
</style>