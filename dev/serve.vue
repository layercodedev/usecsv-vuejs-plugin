<script lang="ts">
import Vue from 'vue';
import UseCSVButton from '../src/UseCSVButton.vue';

export default Vue.extend({
  name: 'ServeDev',
  components: {
    UseCSVButton
  },
  methods: {
    onData: function (data:any) {
      console.log("Data:",data)
    }
  }
});
</script>

<template>
  <div id="app">
    <UseCSVButton importerKey="e1d9bc08-f712-45b2-969e-9ae0bb3b449f" :metadata="{id:'ww'}" :user="{userId:'ss'}" :onData="onData" />
  </div>
</template>
