<template>
    <v-card>
        <v-card-title> <h1>This is NUXT</h1> </v-card-title>

        <v-divider />

        <v-card-text>
            <h2 class="mb-3">
                Is the form valid?
                <span :class="{ 'red--text': !valid, 'green--text': valid }">{{
                    (valid && 'Yes') || 'No'
                }}</span>
            </h2>

            <!--
                The input handler, below, fires every time that the Vuetify validation
                engine has run and produced a validity state value in $event. It is at
                this point that we can modify the form's validity state, as shown.
            -->
            <v-form @input="valid = $event && validTexts">
                <p>
                    Below is a Vuetify v-text-field, which is a "super" version
                    of an input field. We have enabled field validation by
                    setting the <code>:rules</code> prop, as follows:
                    <code> :rules="[v => !!v || 'Required']" </code>
                </p>
                <p>Try deleting the text to see what happens</p>

                <v-text-field
                    ref="fld1"
                    label="text"
                    v-model="text"
                    :rules="[v => !!v || 'Required']"
                    box
                ></v-text-field>
                <br />

                <v-divider />
                <br />

                <h3 class="py-3">
                    The input fields below, in addition to their own validation
                    rules, must both be valid for the form to be valid. <br />
                    This demonstrates how to create multi-field validations and
                    update the form validity based on their result, as well as
                    the individual validation rules.
                </h3>
                <p>
                    Type something into each field and notice the error
                    messages. Once both fields are fully valid then the form
                    will also be valid.
                </p>

                <my-input
                    label="Text2"
                    v-model="text2"
                    :rules="[
                        v => !!v || 'Required',
                        v => v === 'ho' || 'Just enter \'ho\''
                    ]"
                />

                <my-input
                    label="Text3"
                    v-model="text3"
                    :rules="[
                        v => !!v || 'Required',
                        v => v === 'bo' || 'Just enter \'bo\''
                    ]"
                />
            </v-form>
        </v-card-text>
    </v-card>
</template>

<script>
import MyInput from '@/components/my-input'

export default {
    components: { MyInput },

    data() {
        return {
            wide: 150,
            text: 'lala',
            text2: '',
            text3: '',
            valid: false
        }
    },

    methods: {
        log(...args) {
            console.log('LOCAL', ...args)
        }
    },

    computed: {
        validTexts() {
            return this.text2 === 'ho' && this.text3 === 'bo'
        }
    }
}
</script>
