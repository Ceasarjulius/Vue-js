<script   setup>
import { ref } from 'vue';


    const getPrincipal = ref(0);
    const getRate = ref(0);
    const getTime = ref(0);
    const timeUnit = ref('years'); // 'years' or 'months'
    const result = ref(0);

    function handleSubmit() {
      const principal = parseFloat(getPrincipal.value);
      const rate = parseFloat(getRate.value);
      let time = parseFloat(getTime.value);

      // Convert time to years if the selected unit is months
      if (timeUnit.value === 'months') {
        time = (time / 12);
        // console.log(time)
      }

      // Calculate interest
      // console.log(time) // 1
      // console.log(rate) // 10
      // console.log(principal) // 100

      // console.log('The res', (principal * rate * time) / 100);
      
      result.value = (principal * rate * time) / 100;
      // console.log(result.value)
    }


</script>

<template>
  <div class="flex items-center m-12 border box-border w-max h-auto rounded-lg">
    <div>
      <form v-on:submit.prevent="handleSubmit">
        <div class="m-4">
          <label class="block mb-2">Principal:</label>
          <input v-model="getPrincipal" type="number" name="principal" id="principal" class="border border-black rounded-md">
        </div>
        <div class="m-4">
          <label class="block mb-2">Rate:</label>
          <input v-model="getRate" type="number" name="rate" id="rate" class="border border-black rounded-md">
        </div>
        <div class="m-4">
          <label class="block mb-2">Time:</label>
          <input v-model="getTime" type="number" name="time" id="time" class="border border-black rounded-md">
          <select v-model="timeUnit" class="border border-black rounded-md ml-2">
            <option value="years">Years</option>
            <option value="months">Months</option>
          </select>
        </div>
        <button id="submit" name="submit" type="submit" class="border border-sky-300 rounded-2xl px-2 py-1 cursor-pointer hover:bg-slate-300 ml-14">
          Calculate
        </button>
      </form>
    </div>
    <div class="bg-black p-32 m-5">
      <h1 class="text-white">The interest is: {{ result }}</h1>
    </div>
  </div>
</template>
