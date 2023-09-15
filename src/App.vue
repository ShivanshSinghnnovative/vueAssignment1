<template>
  <div class="mainDiv">
    <div class="nameDiv">Name : {{ name }}</div>
    <div class="nameDiv">Address : {{ address }}</div>
    <div class="nameDiv">DOB : {{ DOB.toLocaleDateString() }}</div>
    <button v-on:click="calculateAge()">Get Age</button>
    <div v-if="age !== ''">
      <div class="age">Your current age is : {{ age }}</div>
      <p class="error" v-if="age < 18">you are under age</p>
      <p class="ok" v-else>you are ok to use the website</p>
    </div>
    <div v-for="(user, index) in users" :key="index">
      <div class="data">
        <img :src="user.imageUrl" width="80" height="80"><br/>{{ user.name }} {{ user.age }}
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
      DOB: new Date('12/03/2001'),
      age: "",
      users: [{ name: "Rahul", age: "24", imageUrl: "https://dfstudio-d420.kxcdn.com/wordpress/wp-content/uploads/2019/06/digital_camera_photo-1080x675.jpg" },
      { name: "Rohit", age: "20", imageUrl: "https://helpx.adobe.com/content/dam/help/en/photoshop/using/convert-color-image-black-white/jcr_content/main-pars/before_and_after/image-before/Landscape-Color.jpg" }]
    }
  },
  methods: {
    calculateAge() {
      const birthYear = this.DOB.getFullYear()
      const currentYear = new Date().getFullYear();
      console.log(currentYear, this.DOB)
      this.age = currentYear - birthYear;
    }
  }
}
</script>

<style scoped>
.error {
  color: red;
  font-size: 28px;
  font-weight: 600;
}
img {
  border-radius: 50%;
}
.ok {
  margin-top: 0;
  padding-top: 0;
  color: green;
  font-size: 28px;
  font-weight: 600;
  padding: 10px;
}

.age {
  font-size: 25px;
  color: white;
}
.data {
  color: white;
  margin-bottom: 30px;
  align-items: center;
  font-size: 1.2rem;
  letter-spacing: 1px;
}
.mainDiv {
  width: fit-content;
  text-align: center;
  border: 2px solid rgb(24, 19, 19);
  margin-top: 3%;
  margin-left: auto;
  margin-right: auto;
  background-color: rgb(47, 47, 63);
  border-radius: 5px;
  padding: 1rem 4rem;
  gap: .8rem;
  border: 2px solid gold;
  font-family: cursive;
}
.nameDiv {
  margin-top: 10px;
  color: white;
  margin-bottom: 10px;
  font-size: 25px;
  width: 100%;
  margin-left: 0;
  padding-left: 0;
}
input {
  height: 20px;
  margin-left: 5px;
  margin-right: 5px;
}
button {

  font-size: 1rem;
  padding: 0.5rem 1rem;
  border: 2px solid gold;
  border-radius: 5px;
  letter-spacing: 1px;
  margin-top: 0.8rem;
  font-family: cursive;
  cursor: pointer;
  margin-bottom: .8rem;
}
button:hover {
  background-color: transparent;
  color: white;
}
</style>
