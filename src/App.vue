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
                    <template #default="{ data: albums, loading }">
                        <div class="card">
                            <h1 class="text-2xl font-bold mb-6">Top Death Metal Albums</h1>
                            <div v-if="loading">Loading...</div>
                            <div v-else class="album-grid">
                                <div
                                    v-for="(album, key) in albums"
                                    :key="key"
                                    class="album-grid-item"
                                >
                                    <img :src="album.artwork" />
                                    <h2 class="album-title">{{ album.title }}</h2>
                                    <p class="album-artist">{{ album.artist }}</p>
                                </div>
                            </div>
                        </div>
                    </template>
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
            <!-- 12:this.$el -->
            <div
                class="min-h-0 bg-grey-darker p-4"
                style="border-width: 1px;border-radius: 0.25rem;background: #fff;"
            >
                <div
                    style="width: 420px"
                    class="mx-auto border-l border-r border-dashed border-grey-dark py-4 mb-4"
                >
                    <profile-card></profile-card>
                </div>
                <div
                    style="width: 300px"
                    class="border-l border-r border-dashed border-grey-dark py-4 mx-auto"
                >
                    <profile-card></profile-card>
                </div>
            </div>
            <br />
            <!-- 13:provide & inject -->
            <div class="min-h-0 bg-grey-darker">
                <div class="max-w-sm mx-auto">
                    <accordion-list>
                        <accordion-item :itemId="1">
                            <template #header>Item A</template>
                            <template #content>
                                <span>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec finibus auctor massa, vitae posuere sem tincidunt eget. Duis non vestibulum diam. Pellentesque eleifend interdum mollis. Donec porttitor dui enim. Maecenas a semper sem. Nunc molestie turpis vitae sem auctor, non venenatis velit ultricies.</span>
                            </template>
                        </accordion-item>
                        <accordion-item :itemId="2">
                            <template #header>Item B</template>
                            <template #content>
                                <span>Vestibulum nec urna non nisi viverra vehicula ut sed metus. Cras scelerisque condimentum nunc ut mattis. Curabitur euismod sagittis efficitur. Cras vel orci consectetur, ullamcorper magna vitae, sodales mauris. Aliquam tempus volutpat mi. Nunc vitae molestie ante. In sed varius tortor.</span>
                            </template>
                        </accordion-item>
                        <accordion-item :itemId="3">
                            <template #header>Item C</template>
                            <template #content>
                                <span>Sed porttitor mattis egestas. Duis nec rhoncus ligula. Etiam pellentesque mattis mauris. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Maecenas vel dapibus nulla. Phasellus lobortis nibh et faucibus tincidunt. Phasellus non iaculis turpis, vitae gravida lacus.</span>
                            </template>
                        </accordion-item>
                    </accordion-list>
                </div>
            </div>
            <br />
            <!-- 14:complex -->
            <div class="min-h-0 bg-grey-darker">
                <div class="max-w-sm mx-auto">
                    <div class="card">
                        <h1 class="text-2xl font-bold mb-6">Your Contacts</h1>
                        <sortable-list v-model="contacts">
                            <template #default="{ items: contacts }">
                                <div class="contact-list">
                                    <sortable-item v-for="contact in contacts" :key="contact.id">
                                        <div class="contact-list-item">
                                            <div class="contact-list-contact">
                                                <img
                                                    :src="contact.avatar"
                                                    class="contact-list-avatar"
                                                    alt
                                                />
                                                <div>
                                                    <div
                                                        class="contact-list-name"
                                                    >{{ contact.name }}</div>
                                                    <div
                                                        class="contact-list-email"
                                                    >{{ contact.email }}</div>
                                                </div>
                                            </div>
                                            <sortable-handle>
                                                <svg
                                                    class="contact-list-handle"
                                                    xmlns="http://www.w3.org/2000/svg"
                                                    viewBox="0 0 24 24"
                                                    fill="currentColor"
                                                >
                                                    <path
                                                        fill-rule="evenodd"
                                                        d="M14 4h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1h-2a1 1 0 0 1-1-1V5a1 1 0 0 1 1-1zM8 4h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1H8a1 1 0 0 1-1-1V5a1 1 0 0 1 1-1zm6 6h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1h-2a1 1 0 0 1-1-1v-2a1 1 0 0 1 1-1zm-6 0h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1H8a1 1 0 0 1-1-1v-2a1 1 0 0 1 1-1zm6 6h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1h-2a1 1 0 0 1-1-1v-2a1 1 0 0 1 1-1zm-6 0h2a1 1 0 0 1 1 1v2a1 1 0 0 1-1 1H8a1 1 0 0 1-1-1v-2a1 1 0 0 1 1-1z"
                                                    />
                                                </svg>
                                            </sortable-handle>
                                        </div>
                                    </sortable-item>
                                </div>
                            </template>
                        </sortable-list>
                    </div>
                </div>
            </div>
            <br />
            <!-- 15:complexMax -->
            <div class="max-w-sm mx-auto bg-white rounded shadow-lg p-8" style="height: 36vh;">
                <div>
                    <search-select
                        v-model="selectedBand"
                        :options="bands"
                        :filterFunction="applySearchFilter"
                    ></search-select>
                </div>
                <br />
                <div style="text-align: center;">
                    <button type="button" class="btn btn-blue">Save Changes</button>
                </div>
            </div>
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
    ProfileCard,
    AccordionList,
    AccordionItem,
    SortableList,
    SortableItem,
    SortableHandle,
    SearchSelect
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
        ProfileCard,
        AccordionList,
        AccordionItem,
        SortableList,
        SortableItem,
        SortableHandle,
        SearchSelect
    },
    data () {
        return {
            accountId: 10086,
            date: "Apr 12 2018",
            modalOpen: false,
            tags: ['awesome', 'excellent', 'amazing'],
            contacts: [
                {
                    id: 1,
                    name: 'Alfreda Ferreira',
                    email: 'alfreda.ferreira@example.com',
                    avatar: 'https://randomuser.me/api/portraits/med/women/6.jpg',
                },
                {
                    id: 2,
                    name: 'Leevi Wirtanen',
                    email: 'leevi.wirtanen@example.com',
                    avatar: 'https://randomuser.me/api/portraits/med/men/19.jpg',
                },
                {
                    id: 3,
                    name: 'Kaitlin Sutton',
                    email: 'kaitlin.sutton@example.com',
                    avatar: 'https://randomuser.me/api/portraits/med/women/2.jpg',
                },
                {
                    id: 4,
                    name: 'Alice Wilson',
                    email: 'alice.wilson@example.com',
                    avatar: 'https://randomuser.me/api/portraits/med/women/62.jpg',
                },
                {
                    id: 5,
                    name: 'Etienne Roy',
                    email: 'etienne.roy@example.com',
                    avatar: 'https://randomuser.me/api/portraits/med/men/4.jpg',
                },
            ],
            selectedBand: null,
            bands: [
                'Anthrax',
                'Dark Angel',
                'Destruction',
                'Exodus',
                'Flotsam and Jetsam',
                'Kreator',
                'Megadeth',
                'Metallica',
                'Overkill',
                'Sepultura',
                'Slayer',
                'Testament',
            ],
        }
    },
    methods: {
        applySearchFilter (search, options) {
            return options.filter(option => option.toLowerCase().startsWith(search.toLowerCase()));
        },
    },
}
</script>
