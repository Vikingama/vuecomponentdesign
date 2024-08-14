<script>
export default {
    name: "SortableItem",
    inject: ['sortableListItemClass'],
    mounted () {
        this.$el.classList.add(this.sortableListItemClass);
    },
    render () {
        return this.$scopedSlots.default({})
    }
}
</script>