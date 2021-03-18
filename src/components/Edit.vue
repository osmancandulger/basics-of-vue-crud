<template>
  <div>
    <div id="edit">
      <div class="edit-section">
        <label for="editName">Name:</label>
        <input
          type="text"
          name="editName"
          id="editName"
          placeholder="Edit Name"
          :value="tempName"
          @input="changeInput"
        />
        <label for="editLastname">Last Name:</label>
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

<style lang="scss" scoped>
label {
  font-size: 18px;
  font-weight: 700;
  margin-right: 5px;
}
input + label {
  margin-left: 15px;
}
</style>
