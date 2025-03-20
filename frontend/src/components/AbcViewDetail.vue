<template>

    <v-card outlined>
        <v-card-title>
            Abc # {{$route.params.id }}
        </v-card-title>

        <v-card-text>
            <div>
                <String label="Ddd" v-model="item.ddd" :editMode="editMode" @change="change" />
            </div>
        </v-card-text>
    </v-card>

</template>

<script>
  const axios = require('axios').default;

  export default {
    name: 'AbcViewDetail',
    props: {
      value: Object,
    },
    data: () => ({
        item : [],
    }),
    async created() {
      var params = this.$route.params;
      var temp = await axios.get(axios.fixUrl('/abcs/' + params.id))

      this.item = temp.data;

    },
    methods: {
    }
  }
</script>

