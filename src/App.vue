<template>
  <div id="app">
    <Button @click="displayModal" content="Create Account"/>
    <Modal v-if="modalActive">
      <template v-slot:feature>
        <Feature
          textColor="#866211"
          color="linear-gradient(180deg, #F3D083 38.13%, #F0D08B 100%)"
          cta="Discover the world’s top Designers & Creatives."
          :image="require('@/assets/feature.jpg')"
          creditName="Peter Tarka"
          creditLink="https://dribbble.com/tarka"
        />
      </template>
      <template v-slot:content>
        <SignUpForm />
      </template>
    </Modal>
  </div>
</template>

<script>
import Modal from '@/components/modal';
import SignUpForm from '@/components/signUpForm';
import Feature from '@/components/feature';
import Button from '@/components/button';

export default {
  name: 'app',
  components: {
    Modal,
    SignUpForm,
    Feature,
    Button,
  },
  data () {
    return {
      modalActive: false,
    };
  },
  methods: {
    displayModal () {
      console.log('clicked');
      this.modalActive = true;
    },
  },
};
</script>

<style scoped>
  #app {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    overflow: scroll;
  }
</style>
