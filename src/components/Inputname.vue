<template>
  <div class="inputform">
    <div class="inputname">
      <Checkmark class="checkmarkname" v-if="title" />
      <input
        type="text"
        placeholder="votre nom"
        ref="text"
        v-model="title"
        v-on:input="updateName()"
      />
      <p
        class="material-symbols-outlined close expand inputnameclose"
        v-on:click="clearInput()"
        v-if="this.title !== null"
      >
        close
      </p>
    </div>
  </div>
</template>

<script>
import Checkmark from "./Checkmark.vue";
export default {
  name: "Inputname",
  components: {
    Checkmark,
  },
  data() {
    return {
      title: null,
    };
  },
  methods: {
    updateName() {
      this.$emit("nameChoice", this.title);
    },
    clearInput() {
      this.title = null;
      this.updateName();
    },
  },
};
</script>

<style>
.inputform {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 80%;
  border: 1px solid rgb(211, 211, 211);
  padding: 15px 50px;
  border-radius: 10px;
  text-align: center;
  -webkit-box-shadow: 0px 0px 15px -15px #000000;
  box-shadow: 0px 0px 15px -15px #000000;
}

.inputname {
  display: inline-block;
  width: 80%;
  position: relative;
  border-bottom: 1px solid rgb(199, 199, 199);
}

.inputnameclose {
  top: 5px;
  font-size: 15px;
}

.inputname input {
  border: none;
  width: 90%;
}

textarea:focus,
input:focus {
  outline: none;
}

.checkmarkname {
  position: absolute;
  left: -35px;
  top: 3px;
}

@media screen and (max-width: 540px) {
  .inputform {
    width: 100% !important;
  }
}
</style>
