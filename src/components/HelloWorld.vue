<script>
import contacts from "../../public/contacts.json"
import { ToggleInput } from "./index"

export default {
    name: "HelloWorld",
    components: {
        ToggleInput
    },
    data () {
        return {
            enabled: true,
            contacts
        }
    },
    render (createElement) {
        return createElement("div", {}, [
            createElement(ToggleInput, {
                props: {
                    toggled: this.enabled
                },
                on: {
                    toggle: (v) => {
                        this.enabled = v;
                    }
                }
            }),
            createElement("h1", {}, "Your Contacts"),
            createElement("ul", {}, this.contacts.map(contact => {
                return createElement("li", {}, `${contact.name.first} ${contact.name.last}`)
            })),
            this.$scopedSlots.default({
                subject: "world"
            })
        ])
    }
}
</script>
<style scoped>
h1,
ul,
li {
    user-select: none;
}
ul {
    padding: 0;
    list-style: none;
}
ul > li {
    margin: 1em 0;
    font-weight: bold;
}
</style>