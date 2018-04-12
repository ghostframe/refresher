<template>
  <transition name="fade">
    <div>
      <p class="text-center">{{question.text}}</p>
      <div
        class="btn-group-vertical col"
        role="group"
      >
        <template v-for="(choice, index) in question.choices">
          <button
            type="button"
            class="btn btn-secondary"
            :class="{'btn-success': isRightChoice(index) && revealed,
                     'btn-danger': !isRightChoice(index) && index == selectedIndex}"
            :disabled="revealed"
            @click="selectedIndex = index; revealed = true"
          >
            {{choice}}
          </button>
        </template>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  props: {
    question: {
      type: Object,
      required: true
    }
  },
  data: function() {
    return {
      revealed: false,
      selectedIndex: undefined
    }
  },
  methods: {
    isRightChoice(i) {
      return i == this.question.rightChoiceIndex
    }
  },
  watch: {
    question() {
      this.revealed = false
      this.selectedIndex = undefined
    }
  }
}
</script>

<style>

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}

.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
