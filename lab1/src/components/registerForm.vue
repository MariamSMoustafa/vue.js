<template>
    <div class="buttons">
      <button class="button" @click="selectedComponent = 'adminList'">Admins</button>
      <button class="button" @click="selectedComponent = 'userList'">Users</button>
    </div>
    <br/>
    <div class="form" @submit.prevent="addUser">
      <form>
        <div>
          <label>name</label>
          <input type="text" id="name" v-model="name" />
        </div>
        <br/>
        <div>
          <label>email</label>
          <input type="email" id="email" v-model="email">
        </div>
        <br/>
        <div>
          <label>Role: </label>
          <input type="radio" id="admin" v-model="role" value="admin" />
          <label for="admin">Admin</label>
  
          <input type="radio" id="user" v-model="role" value="user" />
          <label for="user">User</label>
        </div>
        <br/>  
        <button class="button1" type="submit">Add</button>
      </form>
    </div>
    <userList v-if="selectedComponent === 'userList'" :users="users.filter(user => user.role === 'user')" @deleteUser="deleteUser"/>
    <adminList v-if="selectedComponent === 'adminList'" :users="users.filter(user => user.role === 'admin')" @deleteAdmin="deleteUser"/>
</template>
  
  <script>
    import adminList from './adminList.vue';
    import userList from './userList.vue';
    export default {
      name: 'registerForm',
      components: {
        adminList,
        userList,
  },
  data() {
    return {
      name: "",
      email: "",
      role: "",
      users: [],
      selectedComponent:null,
    };
  },
  methods: {
    addUser() {
      const user = {
        name: this.name,
        email: this.email,
        role: this.role,
      };
      this.users.push(user);
      this.name = "";
      this.email = "";
      console.log(user);
    },
    deleteUser(user) {
      const index = this.users.indexOf(user);
      this.users.splice(index, 1);
    },
  },
};
  </script>
  
  <style>
  .form{
    color: #1b203c;
    font-weight: bold;
    font-size: large;
  }
  input{
    margin-left: 7px;
    width: 200px;
    height: 25px;
    border:  solid white;
    border-radius: 5px;
  }
  .button1{
    background-color: #1b203c;
    width: 60px;
    border-radius: 8px;
    border-style: none;
    box-sizing: border-box;
    color: #FFFFFF;
    cursor: pointer;
    display: inline-block;
    font-family: "Haas Grot Text R Web", "Helvetica Neue", Helvetica, Arial, sans-serif;
    font-size: 14px;
    font-weight: bold;
    height: 40px;
    line-height: 20px;
    list-style: none;
    margin-left: 30px;
    outline: none;
    padding: 10px 16px;
    position: relative;
    text-align: center;
    text-decoration: none;
    transition: color 100ms;
    vertical-align: baseline;
    user-select: none;
    -webkit-user-select: none;
    touch-action: manipulation;
  }
   
  .button1:hover,
  .button1:focus {
    background-color: #b1b7d3;
  }
  .button {
    background-color: #1b203c;
    width: 200px;
    border-radius: 8px;
    border-style: none;
    box-sizing: border-box;
    color: #FFFFFF;
    cursor: pointer;
    display: inline-block;
    font-family: "Haas Grot Text R Web", "Helvetica Neue", Helvetica, Arial, sans-serif;
    font-size: 14px;
    font-weight: bold;
    height: 40px;
    line-height: 20px;
    list-style: none;
    margin: 10px;
    outline: none;
    padding: 10px 16px;
    position: relative;
    text-align: center;
    text-decoration: none;
    transition: color 100ms;
    vertical-align: baseline;
    user-select: none;
    -webkit-user-select: none;
    touch-action: manipulation;
  }
  
  .button:hover,
  .button:focus {
    background-color: #b1b7d3;
  }
  </style>
  