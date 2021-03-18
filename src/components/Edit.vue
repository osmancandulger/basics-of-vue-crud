<template>
  <div>
    <div id="edit">
      <div class="edit-section">
        <h1>Edit Name:</h1>
        <input
          type="text"
          name="editName"
          id="editName"
          placeholder="Edit Name"
          :value="tempName"
          @input="changeInput"
        />
        <h1>Edit Lastname:</h1>
        <input
          type="text"
          name="editLastname"
          id="editLastname"
          placeholder="Edit Lastname"
          :value="tempLastname"
          @input="changeInput2"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  el: "#edit",
  // props: {
  //   tempName: String,
  //   tempLastName: String,
  // },
  data() {
    return {
      tempName: "",
      tempLastName: "",
    };
  },
  methods: {
    say(index) {
      console.log("..." + index);
      // eslint-disable-next-line prettier/prettier
    },
    changeInput(event) {
      this.tempName = event.target.value;
      this.$emit("messageChanged", this.tempName);
    },
    changeInput2(event) {
      this.tempLastName = event.target.value;
      this.$emit("messageChanged2", this.tempLastName);
    },
    // eslint-disable-next-line prettier/prettier
  },
};
</script>

<style lang="sass" scoped></style>
