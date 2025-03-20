<template>

    <v-data-table
        :headers="headers"
        :items="ddd"
        :items-per-page="5"
        class="elevation-1"
    ></v-data-table>

</template>

<script>
    const axios = require('axios').default;

    export default {
        name: 'DddView',
        props: {
            value: Object,
            editMode: Boolean,
            isNew: Boolean
        },
        data: () => ({
            headers: [
                { text: "id", value: "id" },
                { text: "ddd", value: "ddd" },
            ],
            ddd : [],
        }),
          async created() {
            var temp = await axios.get(axios.fixUrl('/ddds'))

            temp.data._embedded.ddds.map(obj => obj.id=obj._links.self.href.split("/")[obj._links.self.href.split("/").length - 1])

            this.ddd = temp.data._embedded.ddds;
        },
        methods: {
        }
    }
</script>

