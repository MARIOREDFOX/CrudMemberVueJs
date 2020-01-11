<template>
  <div class="container">
    <div class="card">
      <div class="card-header">
        <h3>Edit Item</h3>
      </div>
      <div class="card-body">
        <form v-on:submit.prevent="updateItem">
          <div class="form-group">
            <label>Name:</label>
            <input type="text" class="form-control" v-model="item.name" />
          </div>
          <div class="form-group">
            <label>Dob:</label>
            {{item.dob}}
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
            <input type="submit" class="btn btn-primary" value="Update Item" />
          </div>
        </form>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      item: {}
    };
  },

  created: function() {
    this.getItem();
  },

  methods: {
    getItem() {
      let uri = "http://localhost:4000/items/edit/" + this.$route.params.id;
      this.axios.get(uri).then(response => {
        this.item = response.data;
      });
    },

    updateItem() {
      let uri = "http://localhost:4000/items/update/" + this.$route.params.id;
      this.axios.post(uri, this.item).then(response => {
        this.$router.push({ name: "Index" });
      });
    }
  }
};
</script>
