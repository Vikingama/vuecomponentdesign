<template>
    <button type="button" @click="confirmDeleteModalOpen = true">
        <slot></slot>
        <confirm-delete-modal
            :show="confirmDeleteModalOpen"
            :accountId="accountId"
            @close="confirmDeleteModalOpen = false"
        ></confirm-delete-modal>
    </button>
</template>
<script>
import { ConfirmDeleteModal } from "./index"

export default {
    name: "DeleteAccountButton",
    components: {
        ConfirmDeleteModal
    },
    props: ["accountId"],
    data () {
        return {
            confirmDeleteModalOpen: false
        }
    },
}
</script>