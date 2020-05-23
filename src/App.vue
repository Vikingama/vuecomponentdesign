<template>
    <div id="app" class="min-h-screen bg-grey-darker p-8">
        <div class="max-w-sm mx-auto">
            <!-- 01:v-model -->
            <user-settings-form :accountId="accountId"></user-settings-form>
            <portal-target name="modals"></portal-target>
            <br />
            <!-- 02:$refs -->
            <div class="card">
                <label class="block">
                    <span class="form-label mb-2">Select a date</span>
                    <date-picker v-model="date" format="MMM D YYYY" :options="{ firstDay: 1 }"></date-picker>
                </label>
            </div>
            <br />
            <!-- 03:nothing -->
            <div class="card justify-center">
                <p class="mb-6">
                    <span>It was the best of times, it was the worst of times, it was the age of wisdom, it was the age of foolishness, it was the epoch of belief, it was the epoch of incredulity, it was the season of Light, it was the season of Darkness, it was the spring of hope, it was the winter of despair, we had everything before us, we had nothing before us, we were all going direct to Heaven, we were all going direct the other way--in short, the period was so far like the present period, that some of its noisiest authorities insisted on its being received, for good or for evil, in the superlative degree of comparison only.</span>
                </p>
                <div class="text-center mb-6">
                    <button @click="modalOpen = true" type="button" class="btn btn-blue">Open Modal</button>
                </div>
                <p class="mb-6">
                    <span>France, less favoured on the whole as to matters spiritual than her sister of the shield and trident, rolled with exceeding smoothness down hill, making paper money and spending it. Under the guidance of her Christian pastors, she entertained herself, besides, with such humane achievements as sentencing a youth to have his hands cut off, his tongue torn out with pincers, and his body burned alive, because he had not kneeled down in the rain to do honour to a dirty procession of monks which passed within his view, at a distance of some fifty or sixty yards. It is likely enough that, rooted in the woods of France and Norway, there were growing trees, when that sufferer was put to death, already marked by the Woodman, Fate, to come down and be sawn into boards, to make a certain movable framework with a sack and a knife in it, terrible in history. It is likely enough that in the rough outhouses of some tillers of the heavy lands adjacent to Paris, there were sheltered from the weather that very day, rude carts, bespattered with rustic mire, snuffed about by pigs, and roosted in by poultry, which the Farmer, Death, had already set apart to be his tumbrils of the Revolution. But that Woodman and that Farmer, though they work unceasingly, work silently, and no one heard them as they went about with muffled tread: the rather, forasmuch as to entertain any suspicion that they were awake, was to be atheistical and traitorous.</span>
                </p>
            </div>
            <announcement-modal :show="modalOpen" @close="modalOpen = false"></announcement-modal>
            <br />
            <!-- 04:nothing -->
            <div class="text-center">
                <primary-button>
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
                        <path d="M13 8V2H7v6H2l8 8 8-8h-5zM0 18h20v2H0v-2z" />
                    </svg>
                    Download
                </primary-button>
            </div>
            <br />
            <!-- 05:v-slot -->
            <div class="mx-auto">
                <media-card>
                    <template #image>
                        <img src="/img/toby.jpg" alt="unsplash" />
                    </template>
                    <template #heading>The Long Road to Mastering the Perfect Cartwheel</template>
                    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Officia eos accusantium minima architecto natus sequi quisquam incidunt dolorem, adipisci accusamus facere dicta magni, qui consectetur, omnis quis, voluptas tempore quo!</p>
                </media-card>
            </div>
            <br />
            <!-- 06:v-slot & renderProps -->
            <contact-list :pseudo-slot="({ contact }) => contact.name.first">
                <template #default="{ item }">
                    <a :href="`/contacts/${item.id}`">{{ item.name.last }}</a>
                </template>
            </contact-list>
            <br />
            <!-- 07:render & createElement & $scopedSlots -->
            <div class="text-center p-8 card">
                <hello-world>
                    <template #default="{ subject }">
                        <strong>Hello {{ subject }}</strong>
                    </template>
                </hello-world>
            </div>
            <br />
            <!-- 08:renderlessComponentBasic -->
            <div class="max-w-md mx-auto">
                <fetch-json url="/albums.json">
                    <div class="card" slot-scope="{ data: albums, loading }">
                        <h1 class="text-2xl font-bold mb-6">Top Death Metal Albums</h1>
                        <div v-if="loading">Loading...</div>
                        <div v-else class="album-grid">
                            <div v-for="(album, key) in albums" :key="key" class="album-grid-item">
                                <img :src="album.artwork" />
                                <h2 class="album-title">{{ album.title }}</h2>
                                <p class="album-artist">{{ album.artist }}</p>
                            </div>
                        </div>
                    </div>
                </fetch-json>
            </div>
            <br />
            <!-- 09:normalInput -->
            <div class="max-w-sm mx-auto card">
                <label class="form-label mb-2">Original Tag Input</label>
                <tag-input v-model="tags"></tag-input>
            </div>
            <br />
            <!-- 10:renderlessComponentAdvanced -->
            <div class="max-w-sm mx-auto card">
                <label class="form-label mb-2">Renderless Tag Input</label>
                <inline-tag-input v-model="tags"></inline-tag-input>
            </div>
            <br />
            <!-- 11:renderlessComponentPlus -->
            <div class="max-w-sm mx-auto card">
                <label class="form-label mb-2">Stacked Tag Input</label>
                <stacked-tag-input v-model="tags"></stacked-tag-input>
            </div>
            <br />
        </div>
    </div>
</template>

<script>
import {
    UserSettingsForm,
    DatePicker,
    AnnouncementModal,
    PrimaryButton,
    MediaCard,
    ContactList,
    HelloWorld,
    FetchJson,
    TagInput,
    InlineTagInput,
    StackedTagInput,
} from "./components"

export default {
    name: 'App',
    components: {
        UserSettingsForm,
        DatePicker,
        AnnouncementModal,
        PrimaryButton,
        MediaCard,
        ContactList,
        HelloWorld,
        FetchJson,
        TagInput,
        InlineTagInput,
        StackedTagInput,
    },
    data () {
        return {
            accountId: 10086,
            date: "Apr 12 2018",
            modalOpen: false,
            tags: ['awesome', 'excellent', 'amazing'],
        }
    }
}
</script>
