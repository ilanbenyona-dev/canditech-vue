<template>
  <div class="section"> 
        <!-- Because the questions -->
        <Question v-for="(question, index) in questions" 
            :key="index"
            :num="index + 1"
            :instructions="question.instructions"
            :type="question.type"
            :dynamic_props="{...question}">
        </Question>
  </div>
</template>

<script>
import Question from '@/components/Questions/AbstractQuestion.vue'
export default {
  components: { Question },
    name: 'AssesmentSection',
    props: {
        title: {
            type: String,
            required: true,
        },
        questions: {
            type: Array, // { type: String, instructions: String, options: Array[String], answer: Number | String }
            required: true
        }
    },
    mounted () {
    }
}
</script>

<style lang="scss">

</style>