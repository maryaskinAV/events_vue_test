<template>
  <div class="list-events">
    <h4>Current Events</h4>
    <div class="event" v-for="event in events" :key="event.id">
      <p>{{ event.title }}</p>
      <span ref="event_delete" @click.prevent="deleteEvent(event)">X</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ListDateEvents',
  props: ['events', 'deleteEvents'],
  watch: {
    events: {
      immediate: true,
      handler(oldValue, newValue) {
        console.log(oldValue, newValue);
      },
    },
  },
  methods: {
    deleteEvent(e) {
      this.deleteEvents(e);
    },
  },
};
</script>
<style lang="scss" scoped>
.list-events {
  width: 100%;
}
.event{
  width: 100%;
  margin: 5px 0;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.5);
  display: flex;
  line-height: 25px;
  & p,span {
    margin: 5px;
  }
  & p {
    flex: 1 0 auto;
  }
}
</style>
