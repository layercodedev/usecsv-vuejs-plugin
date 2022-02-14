<script lang="ts">
import Vue from "vue";
import useCsvPlugin from "@usecsv/js";

type UserObject = {
  readonly userId: string;
};
interface IUsecsv {
  importerKey: string;
  user?: UserObject;
  metadata: Record<string, string | number> | undefined;
}

export default /*#__PURE__*/ Vue.extend<{hasSlot:boolean},{onclick:()=>void,hasScopedSlot:()=>boolean},any,IUsecsv>({
  name: "usecsv-button", // vue component name
  data() {
    return {
      hasSlot: !!this.$slots.default,
    };
  },
  methods: {
    onclick(): void {
      useCsvPlugin({
        importerKey: this.importerKey,
        user: this.importerKey,
        metadata: this.metadata,
      });
    },
    hasScopedSlot(): boolean {
      console.log(this.$scopedSlots.default && this.$scopedSlots.default.name);
      return (
        (this.$scopedSlots.default && this.$scopedSlots.default.name) ===
        "normalized"
      );
    },
  },
});
</script>

<template>
  <div class="usecsv">
    <div v-if="hasScopedSlot()">
      <slot :onclick="onclick"/>
    </div>
    <div v-else>
      <button type="button" id="usecsv-button" @click="onclick">
        <slot> open usecsv </slot>
      </button>
    </div>
  </div>
</template>

<style scoped>
#usecsv-button {
  background-color: #fff;
  color: #000;
  border: 2px solid #000;
  border-radius: 6px;
  padding: 10px 15px;
  text-align: center;
  font-size: 16px;
  cursor: pointer;
}
</style>
