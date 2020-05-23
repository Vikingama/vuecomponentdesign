<script>
export default {
    name: "RenderlessTagInput",
    props: {
        tags: { required: true },
        removeOnBackspace: {
            type: Boolean,
            default: true
        }
    },
    data () {
        return {
            input: ""
        }
    },
    computed: {
        newTag () {
            return this.input.trim();
        }
    },
    methods: {
        addTag () {
            if (this.newTag.length === 0 || this.tags.includes(this.newTag)) {
                return;
            }
            this.$emit("update", [...this.tags, this.newTag])
            this.clearInput();
        },
        removeTag (tag) {
            this.$emit("update", this.tags.filter(v => v !== tag))
        },
        clearInput () {
            this.input = ""
        },
        handleBackspace () {
            if (this.newTag.length === 0) {
                this.$emit("update", this.tags.slice(0, -1))
            }
        }
    },
    render () {
        return this.$scopedSlots.default({
            tags: this.tags,
            addTag: this.addTag,
            removeTag: this.removeTag,
            removeButtonEvents: tag => ({
                click: () => {
                    this.removeTag(tag)
                }
            }),
            inputProps: {
                value: this.input
            },
            inputEvents: {
                input: e => {
                    this.input = e.target.value
                },
                keydown: e => {
                    if (e.key === "Backspace" && this.removeOnBackspace) {
                        this.handleBackspace()
                    }
                    if (e.key === "Enter") {
                        this.addTag();
                        e.preventDefault()
                    }
                },
                blur: () => {
                    this.addTag();
                }
            }
        })
    }
}
</script>