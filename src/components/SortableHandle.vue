<script>
export default {
    name: "SortableHandle",
    inject: ['sortableListHandleClass'],
    mounted () {
        this.$el.classList.add(this.sortableListHandleClass);
    },
    render () {
        return this.$scopedSlots.default({})
    }
}
</script>