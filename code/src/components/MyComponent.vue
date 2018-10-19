<template>
  <div>
    <h3 ref="refTitle">{{titleEx}}</h3>
    <div>
      <input v-model="a1" type="number">
      <button @click="calculate($event)">calculate it</button>
    </div>
    {{resultWordingP}}: <span>{{result}}</span>
  </div>
</template>

<script>
export default {
  props: [
    'titleEx'
  ],
  data: () => ({
    a1: '',
    result: 0,
    resultWording: '',
  }),
  methods: {
    init() {
      console.log('-- my-init --');
    },
    calculate(event) {
      event.preventDefault();
      this.result = +this.a1 + this.result;
      console.log(this.$refs.refTitle);
    }
  },
  created: function () {
    console.log('-- created --');
    this.resultWordingP = '結果';
    // DOM not ready
  },
  mounted: function () {
    console.log('-- mounted --');
    this.init();
    // document.ready()
  },
  destroyed: function () {
    console.log('-- destoryed --');
  },
  watch: {
    a1: (value) => {
      console.log(`watch => ${value}`);
    }
  },
  computed: {
    resultWordingP: {
      //get
      get: function () {
        return this.resultWording;
      },
      //set
      set: function (value) {
        this.resultWording = `${value} => `;
      }
    }
  }
};
</script>

