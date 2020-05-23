<template>
    <renderless-tag-input :tags="tags" @update="(newTags) => $emit('update', newTags)">
        <template #default="{ tags, removeTag, removeButtonEvents, inputProps, inputEvents }">
            <div class="tag-input">
                <span v-for="tag in tags" :key="tag" class="tag-input-tag">
                    <span>{{ tag }}</span>
                    <button
                        type="button"
                        class="tag-input-remove"
                        v-on="removeButtonEvents(tag)"
                    >&times;</button>
                </span>
                <input
                    class="tag-input-text"
                    placeholder="Add tag..."
                    v-bind="inputProps"
                    v-on="inputEvents"
                />
            </div>
        </template>
    </renderless-tag-input>
</template>
<script>
import { RenderlessTagInput } from "./index"

export default {
    name: "InlineTagInput",
    model: {
        prop: "tags",
        event: "update"
    },
    props: ["tags"],
    components: {
        RenderlessTagInput
    }
}
</script>