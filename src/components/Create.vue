<template>
  <div class="container">
    <div class="card">
      <div class="card-header">
        <h3>Add Item</h3>
      </div>
      <div class="card-body">
        <form v-on:submit.prevent="addItem">
          <div class="form-group">
            <label>Name:</label>
            <input type="text" class="form-control" v-model="item.name" />
          </div>
          <div class="form-group">
            <label>Dob:</label>
            <input type="date" class="form-control" v-model="item.dob" />
          </div>

          <div class="form-group">
            <label>Qualification:</label>
            <select
              class="form-control"
              id="exampleFormControlSelect1"
              v-model="item.qualification"
            >
              <option>MCA</option>
              <option>MTECH</option>
              <option>BTECH</option>
            </select>
          </div>

          <div class="form-group">
            <label>Gender:</label>
            <select
              class="form-control"
              id="exampleFormControlSelect2"
              v-model="item.gender"
            >
              <option>Male</option>
              <option>Female</option>
              <option>Others</option>
            </select>
          </div>

          <div class="form-group">
            <input type="submit" class="btn btn-primary" value="Add Item" />
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  components: {
    name: "AddItem"
  },
  data() {
    return {
      item: {}
    };
  },
  methods: {
    addItem() {
      let uri = "http://localhost:4000/items/add";
      this.axios
        .post(uri, this.item)
        .then(response => console.log(response.data));
    }
  }
};
</script>
