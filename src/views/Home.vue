<template>
    <div>
   
        <Counter 
        :year="2026"
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