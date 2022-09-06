<script lang="ts" setup>
import { defineAsyncComponent, h } from 'vue'
const VAceEditor = defineAsyncComponent(() => {
  if (typeof window !== 'undefined') {
    return import('./ace-editor');
  } else {
    return Promise.resolve(defineComponent({
      inheritAttrs: false,
      props: { value: String },
      render() { return h('div', { style: this.$attrs.style, class: this.$attrs.class }, this.value) },
    }) as unknown as typeof import('./ace-editor'));
  }
});
</script>
<template>
  <VAceEditor lang="json" value="{ hello: 'world' }" readonly style="height: 300px" />
</template>
