<template>
  <div class="bigbox">
    <div class="name">Name : {{ name }}</div>
    <div class="name">Address : {{ address }}</div>
    <div class="name">DOB : {{ DOB }}</div>
    <button v-on:click="calculateAge()">Get Age</button>
    <div class="age" v-if="age !== ''">Your current age is : <input v-model="age" readonly></div>
    <p class="under" v-if="age !== '' && age < 18">you are under age</p>
    <p class="ok" v-if="age !== '' && age >= 18">you are ok to use the website</p>

    <div v-for="(user, index) in users" :key="index">
      <div class="data">
        <img :src="user.imageUrl" width="50" height="50">
        {{ user.Name }},{{ user.Age }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      name: "Shivansh Singh",
      address: "Noida",
      DOB: "23/04/2022",
      age: "",
      users: [{ Name: "rahul", Age: "24", imageUrl: "https://dfstudio-d420.kxcdn.com/wordpress/wp-content/uploads/2019/06/digital_camera_photo-1080x675.jpg" },
      { Name: "rohit", Age: "20", imageUrl: "https://helpx.adobe.com/content/dam/help/en/photoshop/using/convert-color-image-black-white/jcr_content/main-pars/before_and_after/image-before/Landscape-Color.jpg" }]
    }
  },
  methods: {
    calculateAge() {
      let date = this.DOB.split("/");
      const saal = date[2];
      this.age = 2023 - saal

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
  color: green;
  font-size: 28px;
  font-weight: 600;
}

.age {
  margin-top: 10px;
  font-size: 25px;
  color: white;
}

.data {
  color: white;
  font-size: 20px;
}

.bigbox {
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
  padding-left: 20px;
  padding-right: 20px;
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
}</style>
