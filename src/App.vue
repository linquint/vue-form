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
    
    <div class="fav-color">
      <p>Favorite color</p> 
      
      <div>
        <input type="radio" name="colorRed" id="colorRed" value="Red" v-model="data.color">
        <label for="colorRed">Red</label>
      </div>
  
      <div>
        <input type="radio" name="colorGreen" id="colorGreen" value="Green" v-model="data.color">
        <label for="colorGreen">Green</label>
      </div>
      
      <div>
        <input type="radio" name="colorBlue" id="colorBlue" value="Blue" v-model="data.color">
        <label for="colorBlue">Blue</label>
      </div>

      <div>
        <input type="radio" name="colorOther" id="colorOther" value="Other" v-model="data.color">
        <label for="colorOther">Other</label>
      </div>
    </div>

    <div>
      <label for="city">City</label>
      <select name="city" id="city" v-model.lazy="data.city">
        <option v-for="i in cities.length" :value="cities[i - 1]">{{ cities[i - 1] }}</option>
      </select>
    </div>

    <div>
      <label for="bio">Bio</label>
      <textarea id="bio" name="bio" v-model="data.bio"></textarea>
    </div>

    <div class="agree-to-terms">
      <label for="terms">Agree to Terms and Conditions</label>
      <input type="checkbox" id="terms" name="terms" v-model="data.terms">
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
        username: "" as string,
        password: "" as string,
        color: undefined as any[] | undefined,
        city: "" as string,
        bio: "" as string,
        terms: false as boolean,
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
      this.data.color = undefined;
      this.data.city = "";
      this.data.bio = "";
      this.data.terms = false;
    },
    submit() {
      
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

form div:not(.fav-color) label {
  display: block;
}

.fav-color div {
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
  height: 5em;
}
</style>
