<template>
    <div class="card">
        <h1 class="text-2xl font-bold mb-6">Your Contacts</h1>
        <div>
            <div v-for="contact in contacts" :key="contact.id" class="flex items-center spaced-y-6">
                <img :src="contact.picture.medium" class="h-12 w-12 rounded-full block mr-2" alt />
                <div>
                    <div class="font-bold">{{ pseudoSlot({ contact: contact }) }}</div>
                    <div class="font-bold">
                        <slot :item="contact"></slot>
                    </div>
                    <div class="text-grey-dark">{{ contact.email }}</div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: "ContactList",
    props: ["pseudo-slot"],
    data () {
        return {
            contacts: []
        }
    },
    created () {
        fetch("/contacts.json").then(res => res.json()).then(data => {
            this.contacts = data;
        }).catch(err => {
            console.error(err)
        })
    }
}
</script>