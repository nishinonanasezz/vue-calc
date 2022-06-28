<template>
  <div class="calculator-border">
    <div class="calculator-display">
      <div class="calculator-formula" v-cloak>{{ formula }}</div>
      <div class="calculator-result" v-cloak>{{ result }}</div>
    </div>

    <div class="calculator-items">
      <div class="calculator-row-1">
        <div class="calculator-item" @click="drop">←</div>
        <div class="calculator-item" @click="clearResult">CE</div>
        <div class="calculator-item" @click="clearAll">C</div>
        <div class="calculator-item" @click="toggle">±</div>
        <div class="calculator-item" @click="square">√</div>
      </div>
      <div class="calculator-row-2">
        <div class="calculator-item" @click="operate(7)">7</div>
        <div class="calculator-item" @click="operate(8)">8</div>
        <div class="calculator-item" @click="operate(9)">9</div>
        <div class="calculator-item" @click="operate('/')">/</div>
        <div class="calculator-item" @click="operate('%')">%</div>
      </div>
      <div class="calculator-row-3">
        <div class="calculator-item" @click="operate(4)">4</div>
        <div class="calculator-item" @click="operate(5)">5</div>
        <div class="calculator-item" @click="operate(6)">6</div>
        <div class="calculator-item" @click="operate('*')">*</div>
        <div class="calculator-item" @click="devided">1/x</div>
      </div>
      <div class="calculator-row-4">
        <div class="calculator-item" @click="operate(1)">1</div>
        <div class="calculator-item" @click="operate(2)">2</div>
        <div class="calculator-item" @click="operate(3)">3</div>
        <div class="calculator-item" @click="operate('-')">-</div>
        <div class="calculator-item" @click="operate('+')">+</div>
      </div>
      <div class="calculator-row-5">
        <div class="calculator-item" @click="operate(0)">0</div>
        <div class="calculator-item" @click="operate('.')">.</div>
        <div class="calculator-item" @click="equal">=</div>

      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "calclator",
  data() {
    return {
      formula: "", // 公式
      result: 0, // result
    };
  },
  methods: {
    devided() {
      this.formula===""||this.formula.endsWith("+"||"-"||"*"||"/"||"%")? {} :  this.formula="1/("+this.formula+")";this.equal();

    },

    // =
    equal() {
      this.result = eval(this.formula)
    },
    // string
    operate(num) {
      this.formula += num
    },

    // <-
    drop() {
      this.formula = this.formula.slice(0,-1);
    },

    // 归零
    clearResult() {
      this.result = 0;
      this.formula = ''
    },
    // 归零
    clearAll() {
      this.formula = null;
      this.result = 0;
    },

    // toggle
    toggle() {
      console.log('toggle');
      this.formula === '' || this.formula.endsWith("+"||"-"||"*"||"/")? {} : this.formula.startsWith("-")?this.formula = Math.abs(eval(this.formula)).toString(): this.formula = "-("+this.formula+")";
      this.equal();
    },

    square() {
      console.log('square');
      eval(this.formula)<0? this.formula = 'Can not suqre the negative value' : this.result=Math.sqrt(eval(this.formula));
    }
  }
};
</script>

<style></style>
<style lang="less" scoped>
.calculator-border {
  .calculator-display {
    width: 92.3%;
    height: 11rem;
    border: 0.2rem solid #b9b4b4;
    background-color: #f5f8f8;
    margin: 1rem auto;
    font-size: 3rem;
    border-radius: 0.5rem;
    box-shadow: 0.2rem 0.2rem 0.5rem #b55858;
    margin-bottom: 2rem;
    .calculator-formula {
      width: 100%;
      height: 42.9%;
      text-align: right;
      box-sizing: border-box;
      padding: 1rem 1.5rem;
      text-overflow: ellipsis;
      white-space: nowrap;
      overflow: hidden;
      color: #ce3b3b;
    }
    .calculator-result {
      width: 100%;
      height: 57.1%;
      line-height: 5rem;
      text-align: right;
      box-sizing: border-box;
      padding: 1.5rem 1rem;
      color: #2a363b;
      text-overflow: ellipsis;
      white-space: nowrap;
      overflow: hidden;
    }
  }
  .calculator-items {
    width: 92.3%;
    height: auto;
    text-align: left;
    margin: 1rem auto;
    .calculator-row-1,.calculator-row-2,.calculator-row-3,.calculator-row-4,.calculator-row-5 {
      margin-top: 1rem;
      width: 100%;
      display: flex;
      justify-content: space-between;
      box-sizing: border-box;
    }
  }

  .calculator-item {
    border: 1px solid rgba(166, 98, 98, 0.74);
    width: 17%;
    height: 4rem;
    display: inline-block;
    text-align: center;
    line-height: 4rem;
    color: #2a363b;
    cursor: pointer;
    border-radius: 0.5rem;
    background-color: rgba(244, 135, 135, 0.78);
    box-shadow: 0.1rem 0.1rem 0.3rem rgba(85, 65, 65);
    transition: all 0.1s linear;
    &:hover {
      color: #f1f5f7;
      box-shadow: 0.3rem 0.3rem 0.5rem #b55858;
    }
    &:active {
      transform: translate(0.05rem, 0.05rem);
    }
  }

  .calculator-row-5 .calculator-item:nth-child(odd) {
    width: 37.2%;
  }
}
</style>
