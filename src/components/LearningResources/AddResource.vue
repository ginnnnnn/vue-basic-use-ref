<template>
  <base-dialog v-if="isInValid" title="Invalid Input" @close="clearError">
    <template #default>
      <p>{{ errorMessage }}</p>
    </template>
    <template #actions>
      <base-button @click="clearError">ok</base-button>
    </template>
  </base-dialog>

  <base-card>
    <form @submit.prevent="handleSubmit">
      <div class="form-control">
        <label for="title">Title</label>
        <input id="title" name="title" type="text" ref="titleInput" />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea
          name="description"
          id="description"
          row="3"
          ref="descriptionInput"
        ></textarea>
      </div>
      <div class="form-control">
        <label for="link">link</label>
        <input id="link" name="link" type="url" ref="linkInput" />
      </div>
      <div>
        <base-button type="submit">Add Resource</base-button>
      </div>
    </form>
  </base-card>
</template>

<script>
import BaseButton from '../UI/BaseButton.vue';
import BaseDialog from '../UI/BaseDialog.vue';
export default {
  components: { BaseDialog, BaseButton },
  inject: ['addResource'],
  data() {
    return {
      titleInput: '',
      descriptionInput: '',
      linkInput: '',
      isInValid: false,
      errorMessage: ''
    };
  },
  methods: {
    clearError() {
      this.errorMessage = '';
      this.isInValid = false;
    },
    handleSubmit() {
      const title = this.$refs.titleInput.value;
      const description = this.$refs.descriptionInput.value;
      const link = this.$refs.linkInput.value;
      if (!title.trim()) {
        this.errorMessage = 'Title must not be empty';
        return (this.isInValid = true);
      }
      if (!description.trim()) {
        this.errorMessage = 'Description must not be empty';
        return (this.isInValid = true);
      }
      if (!link.trim()) {
        this.errorMessage = 'Link must not be empty';
        return (this.isInValid = true);
      }
      this.addResource(title, description, link);
    }
  }
};
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>
