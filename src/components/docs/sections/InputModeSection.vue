<script setup lang="ts">
import { ref } from 'vue';

import Vue2FACodeInput from '@/components/Vue2FACodeInput.vue';
import Section from '@/components/docs/Section.vue';

const generic = ref<string | null>(null);
const numeric = ref<string | null>(null);
</script>

<template>
  <Section title="Input mode" anchor="input-mode">
    <div class="mb-8">
      <p class="mb-2">
        The component is alpha-numerically agnostic and makes no assumptions about the type of characters you auth code
        may contain. Its inner inputs are just regular generic text inputs.
      </p>
      <p class="mb-2">
        On mobile this can be a problem sometimes, though. Depending on your user's phone configuration (browser used,
        keyboard used), it may become annoying for them to switch between keyboard modes. Luckily, you can specify the
        <code>inputmode</code> property (see allowed values
        <a class="underline"
           href="https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/inputMode">here</a>).
      </p>
      <p class="mb-2">
        Realistically, besides the default, which is <code>text</code>, you'll only use <code>numeric</code> for
        all-number auth codes, but any of the listed values can be used. The value you supply just gets passed down to
        the inner inputs.
      </p>
      <p>You can see this difference in action by focusing the two inputs below.</p>
    </div>


    <div class="flex flex-col gap-4 md:flex-row md:gap-0 justify-around">
      <div class="flex flex-col items-center">
        <Vue2FACodeInput v-model="generic" :autofocus="false"/>

        <div class="mt-4">
          <p>Focusing this input should show a generic keyboard on mobile.</p>
        </div>
      </div>

      <div class="flex flex-col items-center">
        <Vue2FACodeInput v-model="numeric" inputmode="numeric" :autofocus="false"/>

        <div class="mt-4">
          <p>Focusing this input should show a numbers-only keyboard on mobile.</p>
        </div>
      </div>
    </div>
  </Section>
</template>
