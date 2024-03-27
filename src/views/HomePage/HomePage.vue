<script lang="ts" setup>
import { computed, ref } from 'vue';

const prompt = ref('');

const isSubmitDisabled = computed(() => prompt.value.length < 15);

const handleSubmit = () => {
  console.log(prompt.value);
};
</script>

<template>
  <div :class="$style.HomePage">
    <div :class="$style.HomePage__container">
      <a href="#">
        <h1 :class="$style.HomePage__h1" class="workbench">
          AiMe
        </h1>
      </a>
      <p>
        AI-powered app for brand owners.
      </p>

      <p :class="$style.HomePage__animatedText">
        I can create a business strategy for you based on the short description you provide.
      </p>

      <textarea
        v-model="prompt"
        :class="$style.HomePage__textarea"
        placeholder="Describe your business..."
      />
      <p
        v-show="isSubmitDisabled"
        :class="$style.HomePage__hintText"
      >
        Please enter a valid prompt (at least 15 characters).
      </p>

      <button
        :class="$style.HomePage__submitButton"
        :disabled="isSubmitDisabled"
        @click="handleSubmit"
      >
        Submit
      </button>
    </div>
  </div>
</template>

<style lang="scss" module>
.HomePage {
  display: flex;
  align-items: center;
  justify-content: center;

  height: 100vh;

  &__h1 {
    font-size: 4rem;
    line-height: 4rem;
    
    animation: colorAnimation 5s infinite;

    @keyframes colorAnimation {
      0% {
        color: var(--c-purple-400);
      }
      50% {
        color: var(--c-purple-500);
      }
      100% {
        color: var(--c-purple-400);
      }
    }
  }

  &__container {
    display: flex;
    flex-direction: column;
    gap: 1rem;

    align-items: center;
    justify-content: center;
    width: 100%;
  }

  &__hintText {
    color: var(--c-grey);
  }
  
    &__textarea {
      width: 100%;
      max-width: 800px;
      height: 200px;
      padding: 24px;
      background: transparent;
      outline: none;
      border-radius: 20px;
      color: var(--c-white);
      font-size: 16px;
      margin-top: 24px;
      border: 1px solid var(--c-purple-400);
      animation: blinkBorder 5s infinite; // Added animation property

    @keyframes blinkBorder {
      0% {
        border-color: var(--c-purple-400);
      }
      50% {
        border-color: var(--c-purple-500);
      }
      100% {
        border-color: var(--c-purple-400);
      }
    }
  }

  &__textarea:hover {
    border-color: var(--c-purple-500); // Change border color on hover
  }

  &__submitButton {
    width: 200px;
    height: 50px;
    background-color: var(--c-purple-400);
    color: var(--c-white);
    font-size: 16px;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    transition: background-color 0.3s ease-in-out; // Added transition property
    margin-top: 24px;

    &:hover {
      background-color: var(--c-purple-500); // Change background color on hover
    }

    &:disabled {
      background-color: var(--c-grey);
      cursor: not-allowed;
    }
    
  }

  p {
    color: var(--c-grey-light);
  }
}
</style>