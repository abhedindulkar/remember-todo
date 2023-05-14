<template>
  <card>
    <div>
      <label for="title"> TITLE </label>
      <input type="text" v-model="title" />
      <label for="description"> DESCRIPTION </label>
      <input type="text" v-model="description" />
      <label for="link"> LINK </label>
      <input type="text" v-model="link" />
      <button @click="addResource__self">ADD RESOURCE</button>
    </div>
    <dialog open v-if="showModal">
      <h1>{{ modalMessage }}</h1>
    </dialog>
  </card>
</template>
<script>
export default {
  inject: ['addResource'],

  data() {
    return {
      title: '',
      description: '',
      link: '',
      showModal: false,
      modalMessage: '',
    };
  },

  methods: {

    addResource__self() {
      if (this.title === '' || this.description === '' || this.link === '') {
        this.modalMessage = 'Input Cannot be empty';
        this.toggleModal();

        setTimeout(this.toggleModal, 2000);
        setTimeout(() => (this.modalMessage = ''), 2000);

        return;
      }

      this.showModal = false;
      this.modalMessage = 'Adding Resource';

      this.toggleModal();
      this.addResource(this.title, this.description, this.link);
      this.emptyInputs();

      setTimeout(this.toggleModal, 2000);
      setTimeout(() => (this.modalMessage = ''), 2000);
    },

    toggleModal() {
      this.showModal = !this.showModal;
    },

    emptyInputs() {
      this.title = '';
      this.description = '';
      this.link = '';
    },
  },
};
</script>
<style scoped>
dialog {
  width: 70%;
  height: auto;
  border-radius: 25px;
  box-shadow: 1px 1px 3px 1px #6c6c7b;
  border: none;
  position: absolute;
  top: 50%;
}
dialog h1 {
  text-align: center;
  color: gray;
}
label {
  font-size: 20px;
  margin: 20px 0;
}
input {
  display: block;
  margin: 10px 0px;
  padding: 10px;
  border-radius: 5px;
  border: 1px solid gray;
  width: 96%;
  box-sizing: border-box;
  outline: none;
}

input[type='text']:focus-visible {
  box-shadow: 1px 1px 3px 1px #6c6c7b;
}
</style>
