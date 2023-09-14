<template>
  <div class="x">
    <div class="name">Name:<input type="text" placeholder="enter name" v-model="name"></div>
    <div class="name">Address:<input type="text" placeholder="enter address" v-model="address"></div>
    <div class="name">DOB:<input type="date" id="dateinput" placeholder="enter DOB" v-model="year"></div>
    <div class="name">Image URL:<input type="text" placeholder="enter image URL" v-model="imageUrl"></div>
    <button v-on:click="calculateAge()">Get Age</button>
    <div v-if="users.length === 1">
      <div v-for="(user, index) in users" :key="index">
        <div>
          <img :src="user.imageUrl" alt="User Image" width="50" height="50">
          Name: {{ user.name }}, Age: {{ user.saal }}
        </div>
      </div>
      <div class="age" v-if="age !== ''">Your current age is : <input v-model="age" readonly></div>
      <p class="under" v-if="age !== '' && age < 18">you are under age</p>
      <p class="ok" v-if="age !== '' && age >= 18">you are ok to use the website</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      name: "",
      address: '',
      year: "",
      age: "",
      users: []
    }
  },
  methods: {
    calculateAge() {
      const selectedDate = new Date(this.year);
      console.log(selectedDate)
      const saal = new Date().getFullYear() - selectedDate.getFullYear();
      console.log(saal)
      this.age = saal
      this.users.push({ name: this.name, saal, imageUrl: this.imageUrl })
      this.name = "";
      this.address = "";
      this.year = "";
      this.imageUrl = "";
    }
  }
}
</script>

<style scoped>
.under {
  color: red;
  font-size: 28px;
  font-weight: 600;
}
.ok {
  font-size: 28px;
  font-weight: 600;
}
.age {
  margin-top: 10px;
  font-size: 25px;
}
.x {
  width: fit-content;
  text-align: center;
  border: 2px solid rgb(24, 19, 19);
  margin-top: 10%;
  margin-left: 35%;
  margin-right: 10%;
  background-color: rgb(47, 47, 63);
}
.name {
  margin-top: 10px;
  color: white;
  margin-bottom: 10px;
  font-size: 25px;
}
input {
  height: 20px;
  margin-left: 5px;
  margin-right: 5px;
}
button {
  height: 35px;
  margin-bottom: 10px;
  font-size: 25px;
}
</style>
