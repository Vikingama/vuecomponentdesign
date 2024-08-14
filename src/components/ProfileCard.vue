<template>
    <with-dimensions>
        <template #default="{ width }">
            <div :class="{ 'profile-card--horizontal': width >= 400 }" class="profile-card">
                <img class="profile-card-image" src="/img/toby.jpg" alt />
                <div class="profile-card-meta">
                    <div class="mb-4">
                        <p class="text-xl leading-tight">Toby Flenderson</p>
                        <p class="text-sm leading-tight text-grey-dark">
                            <span>Human Resources at Dunder Mifflin</span>
                        </p>
                    </div>
                    <div>
                        <button class="btn btn-sm btn-pill btn-indigo-outline">Message</button>
                    </div>
                </div>
            </div>
        </template>
    </with-dimensions>
</template>
<script>
import { WithDimensions } from "./index"

export default {
    name: "ProfileCard",
    components: {
        WithDimensions
    }
}
</script>