<template>
    <div class="question">
        <div class="question__title">
            <div class="question-icon">
                {{ $props.num }}
            </div>
            <div class="question-title">
                {{ $props.instructions }}
            </div>
        </div>
        <component :is="question_types[$props.type]" v-bind="questionProps"></component> 
      </div>
</template>

<script>
import MultipleChoice from "./MultipleChoice.vue";
import SingleChoice from "./SingleChoice.vue";
import OpenText from "./OpenText.vue";

export default {
    components: { MultipleChoice, OpenText, SingleChoice },
    props: {
        num: {
            type: Number,
            required: true
        },
        instructions: {
            type: String,
            required: true
        },
        type: {
            type: String,
            required: true
        },
        dynamic_props: {
            type: Object,
            required: false
        }
    },
    data () {
        return { 
            // No branches :) !!
            question_types: () => ({
                'multiple': MultipleChoice,
                'value': SingleChoice,
                'open_text': OpenText 
            })
        }
    },
    computed: {
        // Inherited props exluding 'AbstractQuestion' props
        questionProps: () => this && this.dynamic_props && this.dynamic_props.filter(p => this.$props[p] === undefined)
    },
    mounted() {
    }
}
</script>


<style lang="scss">

</style>