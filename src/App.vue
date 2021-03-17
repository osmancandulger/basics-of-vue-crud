<template>
  <div id="app">
    <h1>Bind</h1>
    <div id="bind">
      <input
        type="text"
        name="name"
        id="name"
        v-model="name"
        placeholder="Name"
      />
      <input
        type="text"
        name="lastname"
        id="lastname"
        v-model="lastname"
        placeholder="Last Name"
      />
      <input type="button" value="submit" @click="submitItem" />
      <div class="edit-section">
        <h1>Edit Name:</h1>
        <input
          type="text"
          name="editName"
          id="editName"
          v-model="tempName"
          placeholder="Edit Name"
        />
        <h1>Edit Lastname:</h1>
        <input
          type="text"
          name="editLastname"
          id="editLastname"
          v-model="tempLastName"
          placeholder="Edit Lastname"
        />
      </div>

      <table>
        <tr>
          <th>Name</th>
          <th>Last Name</th>
          <th>Actions</th>
        </tr>
        <tr v-for="(item, index) in array" :key="index">
          <td>{{ item.name }}</td>
          <td>{{ item.lastname }}</td>
          <td>
            <input
              class="edit"
              type="button"
              value="Edit"
              @click="editItem(index)"
            />
            <input
              class="delete"
              type="button"
              value="Delete"
              @click="deleteItem(index)"
            />
          </td>
        </tr>
      </table>
    </div>
  </div>
</template>
<script>
export default {
  el: "#app",
  data() {
    /* eslint-disable */
    return {
      name: "",
      lastname: "",
      temp: "",
      data1: "",
      tempName: "",
      tempLastName: "",
      array: [
        {
          name: "Osman Can",
          lastname: "Dülger",
        },
        {
          name: "Arda",
          lastname: "Dülger",
        },
        {
          name: "Namık Kemal",
          lastname: "Dülger",
        },
        {
          name: "Ayşegül",
          lastname: "Dülger",
        },
      ],
    };
  },
  methods: {
    submitItem() {
      if (this.name && this.lastname) {
        this.array.push({ name: this.name, lastname: this.lastname });
        (this.name = null), (this.lastname = null);
      } else {
        alert("Please provide name and lastname !");
      }
    },
    editItem(index) {
      if (this.tempName && !this.tempLastName) {
        this.array[index].name = this.tempName;
      } else if (this.tempLastName && !this.tempName) {
        this.array[index].lastname = this.tempLastName;
      } else if (this.tempName && this.tempLastName) {
        this.array[index].name = this.tempName;
        this.array[index].lastname = this.tempLastName;
      }
      (this.tempName = ""), (this.tempLastName = "");
    },
    deleteItem(index) {
      this.array.splice(index, 1);
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
table {
  font-family: arial, sans-serif;
  border-collapse: collapse;
  width: 100%;
  margin-top: 35px;
}

td,
th {
  border: 1px solid #dddddd;
  text-align: left;
  padding: 8px;
}

.edit {
  background: aliceblue;
  border: none;
  outline: none;
  cursor: pointer;
  padding: 15px;
  border-radius: 25%;
}
.delete {
  background: rgb(240, 180, 180);
  border: none;
  outline: none;
  cursor: pointer;
  padding: 10px;
  border-radius: 25%;
  margin-left: 15px;
}
</style>
