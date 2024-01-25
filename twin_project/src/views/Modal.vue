<template>
    <div v-if="showModal" class="modal">
      <div class="modal-content">
        <div class="modal-header">
          <slot name="header">
            <h3>{{ dynamicHeader }}</h3>
          </slot>

          <a href="#" class="close-x-modal" @click="closeModal()">X</a>
        </div>
  
        <div class="modal-body">
            <component :is="dynamicComponent"></component>
        </div>
  
        <div class="modal-footer">
          <slot name="footer">
            <button class="modal-default-button btn btn-primary" @click="closeModal">
              OK
            </button>
            <button class="modal-default-button btn btn-secondary" @click="closeModal">
              Cancelar
            </button>
          </slot>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        showModal: false,
        dynamicHeader: "Título Padrão",
        dynamicComponent: null
      };
    },
    methods: {
        openModal({ component, header } = {}) {
            this.dynamicHeader = header || "Título Padrão";
            this.dynamicComponent = component || null;
            this.showModal = true;
        },
        closeModal() {
            if (this.$el && this.$el.parentNode) {
              this.showModal = false;
            }
        }
    }
  };
  </script>
