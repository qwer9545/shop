<template>

    <v-data-table
        :headers="headers"
        :items="abc"
        :items-per-page="5"
        class="elevation-1"
    ></v-data-table>

</template>

<script>
    const axios = require('axios').default;

    export default {
        name: 'AbcView',
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
            abc : [],
        }),
          async created() {
            var temp = await axios.get(axios.fixUrl('/abcs'))

            temp.data._embedded.abcs.map(obj => obj.id=obj._links.self.href.split("/")[obj._links.self.href.split("/").length - 1])

            this.abc = temp.data._embedded.abcs;
        },
        methods: {
        }
    }
</script>

