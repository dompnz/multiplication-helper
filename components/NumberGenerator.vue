<template>
  <div class="numbersContainer">
    <div class="numbersInputs">
      <div>
        <span>Number:</span>
        <input v-model.number="baseNumber" type="number" @change="generateNumbers()" />
      </div>
      <div>
        <span>Lines:</span>
        <input v-model.number="numberLines" type="number" @change="generateNumbers()" />
      </div>
    </div>
    <ul class="numbersList">
      <li
        v-for="(number, index) in numbers"
        :class="{ 'lastOfLine': (index+1) % numbersPerLine === 0 }"
      >{{ number }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      baseNumber: 8,
      numberLines: 10,
      numbersPerLine: 10,
      numbers: [],
      items: [{ message: "Foo" }, { message: "Bar" }]
    };
  },
  methods: {
    generateNumbers() {
      this.numbers = [];
      let totalNumbers = this.numberLines * this.numbersPerLine;
      for (let i = 1; i <= totalNumbers; i++) {
        this.numbers.push(i * this.baseNumber);
      }
    }
  },
  created() {
    this.generateNumbers();
  }
};
</script>

<style lang="scss">
$highlight-color: rgba(red, 0.1);
$highlight-color-2: rgba(blue, 0.1);

.numbersContainer {
  width: 100%;
  max-width: 60rem;
  margin: 0 auto;
}

.numbersInputs {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: start;
  margin-bottom: 2rem;

  @media (min-width: 768px) {
    width: 50%;
  }

  & > div {
    width: 100%;
    display: flex;
    align-content: space-between;

    &:not(:last-child) {
      margin-bottom: 0.5rem;
    }

    input {
      margin-left: auto;
      text-align: center;
      background-color: $highlight-color;
    }
  }
}

ul.numbersList {
  display: flex;
  width: 100%;
  flex-direction: row;
  flex-wrap: wrap;
  height: 20rem;
  overflow-y: scroll;
  align-content: start;

  @media (min-width: 768px) {
    width: 100%;
    height: 30rem;
  }

  li {
    --numbers-per-line: 5;
    width: calc(100% / var(--numbers-per-line));
    height: 2rem;
    //background-color: lightcoral;
    border: 1px solid black;
    background-color: $highlight-color-2;
    display: inline;
    // -- center text vertically
    display: flex;
    justify-content: center;
    flex-direction: column;
    // --

    &.lastOfLine {
      font-weight: bold;
      background-color: $highlight-color;
    }

    @media (min-width: 768px) {
      --numbers-per-line: 10;
      height: 3rem;
    }
  }
}
</style>