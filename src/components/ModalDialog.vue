<template>
    <portal to="modals" v-if="show">
        <div class="modal-backdrop">
            <div class="modal">
                <slot></slot>
            </div>
        </div>
    </portal>
</template>
<script>
export default {
    name: "ModalDialog",
    props: ["show"],
    watch: {
        show: {
            immediate: true,
            handler (v) {
                if (v) {
                    document.body.style.setProperty("overflow", "hidden");
                } else {
                    document.body.style.removeProperty("overflow");
                }
            }
        }
    },
    created () {
        const escHandler = e => {
            if (e.key === "Escape" && this.show) {
                this.$emit('close');
            }
        }
        document.addEventListener("keydown", escHandler)
        this.$once("hook:destroyed", () => {
            document.removeEventListener("keydown", escHandler)
        })
    }
}
</script>