<template>

    <v-data-table
        :headers="headers"
        :items="ddddd"
        :items-per-page="5"
        class="elevation-1"
    ></v-data-table>

</template>

<script>
    const axios = require('axios').default;

    export default {
        name: 'DddddView',
        props: {
            value: Object,
            editMode: Boolean,
            isNew: Boolean
        },
        data: () => ({
            headers: [
                { text: "id", value: "id" },
            ],
            ddddd : [],
        }),
          async created() {
            var temp = await axios.get(axios.fixUrl('/ddddds'))

            temp.data._embedded.ddddds.map(obj => obj.id=obj._links.self.href.split("/")[obj._links.self.href.split("/").length - 1])

            this.ddddd = temp.data._embedded.ddddds;
        },
        methods: {
        }
    }
</script>

