<template>
  <div>
    <my-component title-ex="範例1"></my-component>
  </div>
</template>
<script>

import MyComponent from '@/components/MyComponent.vue';

export default {
  components: {
    'my-component': MyComponent,
  },
};
</script>
