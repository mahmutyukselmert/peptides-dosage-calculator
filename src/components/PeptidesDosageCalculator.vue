<template>

  <div style="background-repeat: repeat;
    background-image: url(https://resources.bio-techne.com/bio-techne-assets/images/research-areas/bt-small-molecules-peptides-hero-img.png);">
  </div>

  <div class="peptides-dosage-calculator-area">
    <form @submit.prevent="calculateDosage" class="form-peptides-dosage-calculator">
      <h1>Peptides Dosage Calculator</h1>
      <div class="form-row">
        <label for="syringeVolume">Total syringe volume (ml):</label>
        <select id="syringeVolume" v-model="selectedSyringe" @change="syringeUpdateImageSrc">
          <option value="0.3">0.3 ml</option>
          <option value="0.5">0.5 ml</option>
          <option value="1">1 ml</option>
        </select>
      </div>
      <div class="syringe-images form-row wrap">
        <img
        v-for="syringe in syringes"
        :key="syringe.value"
        :src="syringe.image"
        :alt="syringe.label"
        :class="{'syringe-image-item col': true, 'selected': syringe.value === selectedSyringe }"
        @click="selectSyringe(syringe.value)">
      </div>
      <div class="form-row">
        <label for="peptideAmount">Peptide amount in vial (mg):</label>
        <select id="peptideAmount" v-model="selectedPeptideAmount" @change="highlightSelected">
          <option value="5">5mg</option>
          <option value="10">10mg</option>
          <option value="15">15mg</option>
          <option value="other">Other</option>
        </select>
        <!-- Other seçildiğinde sayısal input alanını göster -->
        <input
          type="number"
          v-if="selectedPeptideAmount === 'other'"
          v-model="otherAmount"
          min="1"
          step="1"
          placeholder="Enter amount"
        />
      </div>
      <div class="form-row">
        <label for="bacteriostaticAmount">Amount of bacteriostatic water (ml):</label>
        <select id="bacteriostaticAmount" v-model="selectedBacteriostaticAmount" @change="highlightSelected">
          <option value="1">1ml</option>
          <option value="2">2ml</option>
          <option value="3">3ml</option>
          <option value="5">5ml</option>
          <option value="other">Other</option>
        </select>
        <!-- Other seçildiğinde sayısal input alanını göster -->
        <input
          type="number"
          v-if="selectedBacteriostaticAmount === 'other'"
          v-model="otherAmount"
          min="1"
          step="1"
          placeholder="Enter amount"
        />
      </div>
      <div class="form-row">
        <label for="peptideDoseAmount">Peptide dose amount (mcg):</label>
        <select id="peptideDoseAmount" v-model="selectedPeptideDoseAmount" @change="highlightSelected">
          <option value="50">50mcg</option>
          <option value="100">100mcg</option>
          <option value="250">250mcg</option>
          <option value="500">500mcg</option>
          <option value="other">Other</option>
        </select>
        <!-- Other seçildiğinde sayısal input alanını göster -->
        <input
          type="number"
          v-if="selectedPeptideDoseAmount === 'other'"
          v-model="otherAmount"
          min="1"
          step="1"
          placeholder="Enter amount"
        />
      </div>
    </form>

    <div class="css-nn2tzi result-box">
      <div class="css-pih1h3 result-area">
        <div class="css-9racl result-text">To have a dose of 50mcg, pull the syringe to 1...</div>
        <div class="css-1mxrc52 result-rule-box">
          <img :src="syringeImageSrc" alt="syringe measurement" class="css-90bm7y result-rule-image">
          <div class="css-fp5dag result-rule-level"></div>
        </div>
      </div>
    </div>

    <p v-if="result">{{ result }}</p>

  </div>
</template>

<script>
export default {
  data() {
    return {
      selectedSyringe: '0.3',
      syringes: [
        { value: '0.3', label: '0.3 ml', image: 'https://storage.googleapis.com/react-app-widgets/peptide-dosage-calc-peptides.org/30-units.f33dc17a.png' },
        { value: '0.5', label: '0.5 ml', image: 'https://storage.googleapis.com/react-app-widgets/peptide-dosage-calc-peptides.org/50-units-1.34ae73d4.png' },
        { value: '1', label: '1 ml', image: 'https://storage.googleapis.com/react-app-widgets/peptide-dosage-calc-peptides.org/u-100-insulin-syringe.a7c72624.png' }
      ],
      selectedPeptideAmount: '5',
      selectedBacteriostaticAmount: '1',
      selectedPeptideDoseAmount: '50',
      otherAmount: 5,
      syringeImageSrc: require('@/assets/images/0.3ml.c3a49644.svg'),
      result: ''
    };
  },
  methods: {
    calculateDosage() {
      // Hesaplama mantığını burada uygulayın
      // Örneğin: this.result = this.selectedSyringe * 10;
      // Gerçek hesaplama mantığını ekleyin
    },
    selectSyringe(value) {
      this.selectedSyringe = value;
      this.syringeUpdateImageSrc();
    },
    syringeUpdateImageSrc() {
      switch (this.selectedSyringe) {
        case '0.3':
          this.syringeImageSrc = require('@/assets/images/0.3ml.c3a49644.svg');
          break;
        case '0.5':
          this.syringeImageSrc = require('@/assets/images/0.5ml.29345c9e.svg');
          break;
        case '1':
          this.syringeImageSrc = require('@/assets/images/1ml.92fc4165.svg');
          break;
        default:
          this.syringeImageSrc = require('@/assets/images/0.3ml.c3a49644.svg');
      }
    },
    selectPeptideAmount(value) {
      this.selectedPeptideAmount = value;
    },
    selectBacteriostaticAmount(value) {
      this.selectedBacteriostaticAmount = value;
    },
    selectPeptideDoseAmount(value) {
      this.selectedPeptideDoseAmount = value;
    },
    highlightSelected() {
      // Seçilen şırıngayı ön plana çıkarmak için gerekli işlemleri yapabilirsiniz
    }
  }
};
</script>

<style lang="scss">
  @import '@/assets/css/styles.scss';
</style>

