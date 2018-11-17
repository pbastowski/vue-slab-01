<template>
    <!--
        We bind to $attrs, $listeners and value to enable normal Vuetify v-input functionality
        on our custom input field.
    -->
    <v-input
        :value="value"
        v-bind="$attrs"
        v-on="$listeners"
        style="height: 84px;"
    >
        <!--
            We implement the floating label ourselves by hooking into the focus and blur
            events and applying the correct "float" to the label.
        -->
        <label :for="_uid" :class="{ float: floatLabel }">{{ label }}</label>

        <input
            :id="_uid"
            v-bind="$attrs"
            v-on="
                Object.assign({}, $listeners, {
                    // We override the input event handler, because v-model
                    // expects input to be a value not an event object.
                    input(e) {
                        $emit('input', e.target.value)
                    }
                })
            "
            @focus="
                floatLabel = true
                $emit('focus', $event)
            "
            @blur="
                floatLabel = !!value
                $emit('blur', $event)
            "
            :value="value"
        />
    </v-input>
</template>

<script>
export default {
    props: {
        value: String,
        label: String,
        hint: String
    },

    data() {
        return {
            floatLabel: false
        }
    }
}
</script>

<style scoped lang="scss">
label {
    user-select: none;
    transition: all 0.25s;
    position: absolute;
    margin-left: 10px;
}

label.float {
    margin-top: -15px;
    font-size: 12px;
}

input {
    min-height: 54px !important;
    border: 1px solid silver;
    padding: 3px 8px;
    font-size: 16px;
}
</style>
