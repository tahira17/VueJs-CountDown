<template>
    <h1 class="border-1 my-8 border-gray-400 sm:w-4/12 mx-auto">This coundown app shows countdown until a specific time, as of now the time given is 25-feburary-2025</h1>
  <br>
    <div   class="text-center mb-3 bg-blue-300 mb-4 p-2 rounded-md shadow-md border-1 my-8 border-gray-400 sm:w-6/12 mx-auto">
   
        <Counter 
        :year="2025"
        :month="2"
        :date="25"
        :hour="17"
        :minute="19"
        :second="0"
        :milisecond="0"
         />
    </div>
</template>

<script>
import Counter from '@/components/Counter.vue'
export default {
    components: {
        Counter
    }
}
</script>

<style lang="scss" scoped></style>