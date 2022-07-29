<template>
  <div>
    <div>
      <input class="showname" type="text" @change="onchange" v-model="val">
      <button class="addname">Add</button>
    </div>
    <div>
      <select name="Name" id="dropdown">
        <option value="name">Name</option>
        <option value="Bret">Bret</option>
        <option value="Antonette">Antonette</option>
        <option value="Samantha">Samantha</option>
      </select>
    </div>
      <dir>
        <ul>
          <li>
            <span class="titel">Name:</span>
            <span class="detail"></span>
            <span class="titel">Email:</span>
            <span class="detail"></span>
            <span class="titel">City:</span>
            <span class="detail"></span>
          </li>
        </ul>
      </dir>
    
  </div>
</template>

<script>
import { ref, onMounted, axios } from "vue";
export default {
  setup() {
    const result = ref(null);
    const val = ref("");
    onMounted(async () => {
      result.value = await axios.get('https://jsonplaceholder.typicode.com/users');

    })
    //  onchange(async()=>{
    //   console.log("hiii",val.value)
    //   result.value = await axios.get('https://jsonplaceholder.typicode.com/users');
    //  })

    return {
      result,
      val,
      onchange
    }
  }
}
</script>

<style>
.showname {
  border: none;
  border-bottom: 2px solid black;
  width: 220px;
  margin: 39px;
  height: 50px;
}

.addname {
  width: 50px;
  height: 30px;
  border-radius: 5px;

}
</style>