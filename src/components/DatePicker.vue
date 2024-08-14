<template>
    <input
        :value="value"
        id="datePicker"
        ref="input"
        type="text"
        class="form-input"
        placeholder="YYYY-MM-DD"
    />
</template>
<script>
import Pikaday from 'pikaday';

export default {
    name: "DatePicker",
    props: {
        value: { required: true },
        format: { default: 'YYYY-MM-DD' },
        options: { default: {} },
    },
    mounted () {
        const picker = new Pikaday({
            field: this.$refs.input,
            format: this.format,
            onSelect: () => {
                this.$emit("input", picker.toString())
            },
            ...this.options
        })
    }
}
</script>