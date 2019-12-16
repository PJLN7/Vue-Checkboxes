<template>
<div class="main" v-bind:class="{'expanded':selectedNames.length}">
  <h1 id="user-header">Users</h1>
  <div class="content">
    <div class="btn-options">
      <button @click="selectAll">Select All</button>
      <button @click="removeAll">Remove All</button>
    </div>
    <div class="user-list-main" v-bind:class="{'expanded':selectedNames.length}">
      <div class="user-item" v-bind:key="user.id" v-for="user in users">
        <input type="checkbox" v-bind:value="user.id" v-model="selectedNames" />
        <span class="checkmark" v-if="selectedNames.includes(user.id)"></span>
        <span class="empty-checkbox" v-else></span>
        <label class="user-name" v-bind:class="{'active': selectedNames.includes(user.id)}" v-bind:for="user.name">{{user.name}}</label>
      </div>
    </div>
    <div class="selected-names">
      <h1 id="selected-header">Selected Users
        <h1>
          <pre class="selected-names-text" v-if="selectedNames.length">
          {{selectedNames}}
</pre>
          <pre class="selected-names-text" v-else>No names selected</pre>
    </div>
  </div>
</div>
</template>

<script>
export default {
    el: ".main",
  methods: {
    selectAll() {
      this.users = this.users.map(user => {
        const idIdx = this.selectedNames.indexOf(user.id);
        if (idIdx !== -1) return user;
        else {
          user.isActive = true;
          this.selectedNames.push(user.id);
          return user;
        }
      });
    },
    removeAll() {
      this.users = this.users.map(user => {
        user.isActive = false;
        return user;
      });
      this.selectedNames = [];
    }
  },
  data: function() {
    return {
      users: [
        {
          id: "01bbb998-af3d-47a4-b0ff-e67d033d80e9",
          name: "Luz Ballard",
          isActive: false
        },
        {
          id: "01021494-f157-4183-964c-6b0ddc964ab8",
          name: "Corey Johnson",
          isActive: false
        },
        {
          id: "97a2daa4-406b-4b1c-831e-bdfd90b224f2",
          name: "Andrew Torres",
          isActive: false
        },
        {
          id: "6256ba85-b59f-40b9-8715-406cc54d7f05",
          name: "Nichole Wilson",
          isActive: false
        },
        {
          id: "5c0c746c-ec56-4fb7-8b32-066b64d70611",
          name: "Nancy Hall",
          isActive: false
        },
        {
          id: "c103b480-8efb-450f-9141-6a8037de2348",
          name: "Agnes Lorenzen",
          isActive: false
        },
        {
          id: "4e0cc3dc-fce9-45d9-85c7-a3ae5cb0ce57",
          name: "Donald Hyde",
          isActive: false
        },
        {
          id: "f80af139-5c68-4475-8cb6-ced7e38c6f43",
          name: "Dennis Fuller",
          isActive: false
        },
        {
          id: "5073359e-b228-4852-b1a3-3f2edfc8672f",
          name: "Francis Hodgkins",
          isActive: false
        },
        {
          id: "9c9a3cc8-044e-43d0-87ff-58a6b44eca53",
          name: "David McLain",
          isActive: false
        }
      ],
      selectedNames: []
    };
  }
}
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Raleway", sans-serif;
  background: #121212;
}

.main {
  width: 50%;
  height: 60vh;
  margin: 2% auto;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.5);
  border-radius: 5px;
  background: #212121;
}

.expanded {
  max-height: 85vh;
}

#user-header {
  background: black;
  color: #e0e0e0;
  text-align: center;
  padding: 2% 0;
}

.btn-options {
  display: flex;
  justify-content: space-between;
  width: 100%;
}

button {
  background: #e0e0e0;
  color: black;
  font-size: 1rem;
  border: none;
  width: 49.9%;
  padding: 2%;
  font-weight: bold;
  cursor: pointer;
}

.user-list-main {
  display: flex;
  width: 100%;
  height: 50%;
  flex-wrap: wrap;
  overflow-y: auto;
}

.user-item {
  position: relative;
  width: 50%;
  margin: 0 auto;
  padding: 2.5% 0;
  border: 1px solid;
  background: #212121;
}

input {
  position: absolute;
  cursor: pointer;
  opacity: 0;
  z-index: 4;
  top: 15px;
  left: 15px;
  height: 25px;
  width: 25px;
}

.checkmark,
.empty-checkbox {
  position: absolute;
  border-radius: 3px;
  top: 15px;
  left: 15px;
  height: 25px;
  width: 25px;
  background: #e0e0e0;
  z-index: 1;
}

.checkmark:after {
  content: "";
  position: absolute;
  left: 9px;
  top: 5px;
  width: 5px;
  height: 10px;
  border: solid #212121;
  border-width: 0 3px 3px 0;
  transform: rotate(45deg);
}

button:hover {
  opacity: 0.7;
}

.user-name {
  color: #616161;
  margin-left: 25%;
  font-size: 1.25rem;
  background: #212121;
  font-weight: bold;
}

.active {
  color: #e0e0e0;
}

.selected-names {
  width: 100%;
  height: 100%;
  background: #212121;
}

#selected-header {
  background: black;
  color: #e0e0e0;
  text-align: center;
  padding: 2% 0;
}

.selected-names-text {
  text-align: center;
  font-size: 1rem;
  padding: 2% 0;
  width: 100%;
  color: #e0e0e0;
  background: #212121;
}
</style>