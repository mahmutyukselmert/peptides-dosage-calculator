<!-- src/App.vue -->
<template>
  <PeptidesDosageCalculator />
  <footer>
    <p class="copyright-text">
      2024 Powered by <a href="https://www.linkedin.com/in/mahmutyukselmert" target="_blank">Mahmut Yüksel MERT</a>
    </p>
  </footer>
</template>

<script>
import PeptidesDosageCalculator from './components/PeptidesDosageCalculator.vue';

export default {
  components: {
    PeptidesDosageCalculator
  }
};
</script>