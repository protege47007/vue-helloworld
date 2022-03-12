<template>
  <div>
      <form @submit.prevent="submitForm">
          <label>Name</label>
          <input type="text" v-model="name">
            <br>

          <label>Mail</label>
          <input type="mail" v-model="mail">
            <br>
            <label>password</label>
          <input type="password" v-model="password" >
            <br>
          <label>Skill</label>
          <input type="text" v-model="temp" @keyup="setSkill">
            <br>
          <label>Location</label>
          <select v-model="state" >
              <option :value="city.name" v-for="city in cities" :key="city.id">{{city.name}}</option>
          </select>


      </form>
      <div>
          <p>Name: {{name}}</p>
          <p>Mail: {{mail}}</p>
          <p>Location: {{state}}</p>
          <p>Password: {{password}}</p>
          <div v-if="skills">
              <p v-for="(skill, i) in skills" :key="i" >{{skill}}</p>
          </div>
          
      </div>
  </div>
</template>

<script>
export default {
    data: () => ({
        cities: [
            {name: "Lagos", id: 123},
            {name: "Ota", id: 788},
            {name: "Abeokuta", id: 234}
        ],
        password: '',
        mail: '',
        name: '',
        state: '',
        temp: '',
        skills: [],
    }),
    methods: {
        submitForm(){

        },

        setSkill(e){
            if(e.key == "Enter" && this.temp){
                this.skills.push(this.temp)
                this.temp = ""
            }
        }

    }
}
</script>

<style>

</style>