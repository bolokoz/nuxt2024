<script setup>
const route = useRoute()
const id = ref(route.params.id)

    const authHeaders = { Authorization: `Bearer b87386ef-d655-411a-808a-cd70bd0bf9f3`}
    const {data: items, pending, error} = await useFetch(`https://coda.io/apis/v1/docs/KGZDix4HIW/tables/Reviews/rows/${id.value}?valueFormat=rich`, {
        headers: authHeaders
    })
</script>

<template>

<pre>{{ items }}</pre>

</template>