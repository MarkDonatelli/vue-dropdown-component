<template>
  <div class="min-h-screen flex items-center justify-center bg-slate-200 px-4">
    <div class="flex gap-5">
      <List :dropdown-values="dropdownValues">
        <template v-slot:title> Dropdown One</template>
      </List>

      <List :dropdown-values="dropdownValuesTwo">
        <template v-slot:title> Dropdown Two</template>
      </List>
    </div>
  </div>
</template>

<script>
import List from './components/List.vue';

export default {
  components: {
    List,
  },
  data() {
    return {
      dropdownValues: ['Option 1', 'Option 2', 'Option 3', 'Option 4'],
      dropdownValuesTwo: ['Option 5', 'Option 6', 'Option 7', 'Option 8'],
    };
  },
  methods: {},
};
</script>

>
