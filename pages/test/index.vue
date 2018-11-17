<template>
    <div>
        <h1>This is /test</h1>
        <pre>{{ getA }}</pre>
        <pre>{{ getA }}</pre>
        <pre>{{ getA }}</pre>
        <pre>{{ getA }}</pre>
    </div>
</template>

<script>
export default {
    data() {
        return {
            a: [1, 2, 3]
        }
    },

    computed: {
        getA() {
            return this.a
        }
    }
}
</script>
