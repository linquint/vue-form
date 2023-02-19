<template>
  <form @submit.prevent @reset="() => reset()">
    <div>
      <label for="formInput">Username</label>
      <input type="text" id="formInput" name="formInput" v-model="data.username">
    </div>

    <div>
      <label for="password">Password</label>
      <input type="password" name="password" id="password" v-model="data.password">
    </div>
    
    <div class="age-group">
      <p>Age group</p> 
      
      <div>
        <input type="radio" name="formRadio" id="radioYes" value="Yes" v-model="data.radio">
        <label for="radioYes">Yes</label>
      </div>
  
      <div>
        <input type="radio" name="formRadio" id="radioNo" value="No" v-model="data.radio">
        <label for="radioNo">No</label>
      </div>
      
      <div>
        <input type="radio" name="formRadio" id="radioMaybe" value="Maybe" v-model="data.radio">
        <label for="radioMaybe">Maybe</label>
      </div>
    </div>

    <div>
      <label for="city">City</label>
      <select name="city" id="city" v-model.lazy="data.city">
        <option v-for="i in cities.length" :value="cities[i - 1]">{{ cities[i - 1] }}</option>
      </select>
    </div>

    <div>
      <label for="formTextarea">Bio</label>
      <textarea id="formTextarea" name="formTextarea" v-model="data.bio"></textarea>
    </div>

    <div class="agree-to-terms">
      <label for="formCheckbox">Agree to Terms and Conditions</label>
      <input type="checkbox" id="formCheckbox" name="formCheckbox" v-model="data.checkbox">
    </div>
    
    <button type="reset">Reset</button>
  </form>

  <pre>{{ data }}</pre>
</template>

<script lang="ts">
export default {
  data() {
    return {
      data: {
        username: "",
        password: "",
        radio: undefined,
        city: "",
        bio: "",
        checkbox: false,
      },
      cities: [
        "", "Alytus", "Jonava", "Kaunas", "Klaipėda", "Marijampolė", "Mažeikiai", "Panevėžys", "Šiauliai", "Utena", "Vilnius"
      ],
    }
  },
  methods: {
    reset() {
      this.data.username = "";
      this.data.password = "";
      this.data.radio = undefined;
      this.data.city = "";
      this.data.bio = "";
      this.data.checkbox = false;
    }
  }
}
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
  gap: 1em;
  background-color: var(--background);
  border-radius: 1em;
  padding: 1.5em;
  text-align: left;
  color: var(--text);
}
form * {
  transition: all .2s;
  box-sizing: border-box;
  color: var(--text);
}

form div:not(.age-group) label {
  display: block;
}

.age-group div {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
}

.agree-to-terms {
  display: flex;
  flex-direction: row-reverse;
  justify-content: flex-end;
}

input[type=text], input[type=password], select, textarea {
  padding: 0.5em;
  border-radius: 0.25em;
  border: 0.2em solid transparent;
  outline: none;
  background-color: var(--input);
  width: 100%;
}
input[type=text]:focus, input[type=password]:focus, select:focus, textarea:focus {
  border-color: var(--accent);
}

textarea {
  resize: none;
  height: 8em;
}

.output {
  display: flex;
  flex-direction: column;
}
</style>
