<template>
  <div class="backdrop" @click.self="closeModal">
    <div class="modal" :class="{ sale: theme === 'sale' }">
      <slot>This is the default Content</slot>
      <div class="actions">
        <slot name="links"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["title", "content", "theme"],
  methods: {
    closeModal() {
      this.$emit("close");
    },
  },
};
</script>

<style>
.modal {
  background: #fff;
  padding: 20px;
  margin: 200px auto;
  width: 400px;
  border-radius: 10px;
}

.backdrop {
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  top: 0;
  height: 100%;
  width: 100%;
}

.modal h1 {
  color: #03cfb4;
  border: none;
  padding: 0;
}

.modal .actions {
  text-align: center;
  margin: 30px 0 10px 0;
  color: #333;
}

.modal .actions a {
  color: #333;
  padding: 8px;
  border: 1px solid #eee;
  border-radius: 4px;
  text-decoration: none;
  margin: 10px;
}

/* sale styles */
.modal.sale {
  background: crimson;
  color: #fff;
}
.modal.sale h1 {
  color: #fff;
}
.modal.sale .actions {
  color: white;
}
.modal.sale .actions a {
  color: white;
}
</style>
