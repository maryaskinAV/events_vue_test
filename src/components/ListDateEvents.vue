<template>
  <div class="list-events">
    <h4>Current Events</h4>
    <div class="event" v-for="event in events" :key="event.id">
      {{ event.title }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'ListDateEvents',
  props: ['events'],

};
</script>
<style lang="scss" scoped>
.list-events {
}
</style>
