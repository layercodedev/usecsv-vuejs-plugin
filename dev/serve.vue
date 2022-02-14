<script lang="ts">
import Vue from 'vue';
import Usecsv from '@/usecsv.vue';

export default Vue.extend({
  name: 'ServeDev',
  components: {
    Usecsv
  }
});
</script>

<template>
  <div id="app">
    <usecsv />
  </div>
</template>
