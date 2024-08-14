<template>
    <renderless-tag-input
        :tags="tags"
        :remove-on-backspace="false"
        @update="(newTags) => $emit('update', newTags)"
    >
        <template #default="{ tags, addTag, removeButtonEvents, inputProps, inputEvents }">
            <div class="stacked-tag-input">
                <div class="stacked-tag-input-form">
                    <input
                        class="form-input"
                        placeholder="Add tag..."
                        v-bind="inputProps"
                        v-on="inputEvents"
                    />
                    <button class="btn btn-indigo" @click="addTag">Add Tag</button>
                </div>
                <ul class="stacked-tag-list">
                    <li v-for="tag in tags" :key="tag">
                        {{ tag }}
                        <button
                            type="button"
                            class="stacked-tag-link"
                            v-on="removeButtonEvents(tag)"
                        >Remove</button>
                    </li>
                </ul>
            </div>
        </template>
    </renderless-tag-input>
</template>

<script>
import { RenderlessTagInput } from './index';

export default {
    name: 'StackedTagInput',
    components: {
        RenderlessTagInput,
    },
    model: {
        prop: 'tags',
        event: 'update',
    },
    props: {
        tags: { required: true },
    },
};
</script>
<style scoped>
ul {
    padding: 0;
    list-style: none;
}
ul > li {
    padding: 0 16px;
    height: 36px;
    border-width: 1px;
    border-radius: 0.25rem;
    line-height: 36px;
}
</style>