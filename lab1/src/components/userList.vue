<template>
    <div>
      <h2>Users</h2>
    <ul>
      <h3 v-for="user in users" :key="user.name">
        {{ user.name }} - {{ user.email }}
        <button class="button" @click="$emit('deleteUser', user)">Delete</button>
      </h3>
    </ul>
    </div>
</template>
  
  <script>

    export default {
      name: 'userList',
      emits:['deleteUser'],
    props: {
      users: {
        type: Array,
        required: true,
      },
    },
    data() {
      return {
      };
    },
    methods: {
    },
    }
  </script>
  
  <style>
  .button {
    background-color: #1b203c;
    width: 100px;
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
  