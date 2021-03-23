<template>
  <div class="notes">
    <!-- Posts -->
    <div class="note card mb-2" v-for="(note, index) in notes" :key="index">
      <div class="card-body">
        <div class="header-note">
          <h3 class="card-title">{{ note.title }}</h3>
          <p
            class="remove-block"
            style="cursor: pointer"
            @click="removePost(index)"
          >
            X
          </p>
        </div>
        <h6 class="card-subtitle mb-2 text-muted">{{ note.sub }}</h6>
        <p class="card-text">{{ note.descr }}</p>
        <a href="#" class="card-link">{{ note.date }}</a>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  props: {
    notes: {
      type: Array,
      required: true,
    },
  },

  methods: {
    removePost(index) {
      this.$emit('remove', index);
    },
  },
};
</script>


<style lang="scss">
.notes {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  padding: 40px 0;
}

.note {
  width: 48%;
  padding: 18px 20px;
  margin-bottom: 20px;
  background-color: #fff;

  p {
    margin: 16px 0;
  }

  a {
    font-size: 14px;
    color: grey;
  }

  h3 {
    color: #402caf;
    font-size: 22px;
    font-weight: 600;
  }
}

.header-note {
    .remove-block {
        position: relative;
        top: -15px;
        &:hover {
            color: red;
            transition: ease 0.3s;
            transform: scale(1.1);
        }
    }
  display: flex;
  justify-content: space-between;
}
</style>