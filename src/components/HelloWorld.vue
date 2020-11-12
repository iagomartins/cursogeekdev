<template>
  <div class="container-fluid">
    <h1>{{ msg }}</h1>

    <div class="alert alert-warning" role="alert" v-show="users.length == 0">
      There isn't users anymore!
    </div>

    <table class="table table-striped" v-show="users.length > 0">
      <thead>
        <tr>
          <td>#</td>
          <td>Name</td>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(user, index) in users" v-bind:key="user.id">
          <td>{{ user.id }}</td>
          <td>{{ user.name }}</td>
          <td>
            <button class="btn btn-danger" @click="deleteUser(index)">Remove</button>
          </td>
        </tr>
      </tbody>
    </table>

    <div class="form-group">
      <input v-model="id" type="text" class="form-control mb-3" placeholder="Type an ID" name="userID">
      <input v-model="name" type="text" class="form-control mb-3" placeholder="Type a name" name="userName">
      <button class="btn btn-success" @click="addUser()">Add</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      title: "Curso GeekDev",
      users: [
        { id:1, name: 'João' },
        { id:2, name: 'Luiz' },
        { id:3, name: 'Pedro' },
        { id:4, name: 'Maria' }
      ],
      id: '',
      name: ''
    }
  },
  methods: {
    deleteUser(id) {
      this.users.splice(id, 1);
    },
    addUser() {
      this.users.push({
        id: this.id,
        name: this.name
      });
      this.id = '';
      this.name = '';
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
