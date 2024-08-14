<script>
export default {
    name: "FetchJson",
    props: ["url"],
    data () {
        return {
            data: null,
            loading: true
        }
    },
    created () {
        fetch(this.url).then(res => res.json()).then(data => {
            setTimeout(() => {
                this.data = data;
                this.loading = false
            }, 3000)
        }).catch(err => {
            console.error(err)
        })
    },
    render () {
        return this.$scopedSlots.default({
            data: this.data,
            loading: this.loading
        })
    }
}
</script>