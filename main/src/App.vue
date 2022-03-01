<template>
  <div>
    <Fio lastName="Буторин" firstName="Дэниель" middleName="Михайлович"/>
    <Vyatsu :results="results"/>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import axios from 'axios';
import Fio from '../../fio/src/main';
import Vyatsu from '../../vyatsu/src/main';

const url = 'http://localhost:8080/admission/';
export default {
  name: 'App',
  props: {
    results: [],
  },
  components: {
    Fio,
    Vyatsu,
  },
  mounted() {
    axios
      .get(url)
      .then((response) => {
        console.log(response);
        this.results = response.data;
      })
      .catch((error: any) => console.log(error));
  },
};
</script>
