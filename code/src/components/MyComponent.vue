<template>
  <div>
    <h3 ref="refTitle">{{titleEx}}</h3>

    <div class="d-flex justify-content-center">
      <form class="form-inline">
        <div class="form-group mx-sm-3 mb-2">
          <label for="inputPassword2" class="sr-only">數字</label>
          <input type="number" class="form-control" v-model="a1" placeholder="">
        </div>
        <button type="submit" class="btn btn-primary mb-2" @click="calculate($event)">calculate it</button>
      </form>
    </div>
    <div>
      {{resultWordingP}}: <span>{{result}}</span>
    </div>

  </div>
</template>

<script>
export default {
  props: [
    'titleEx',
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
    },
  },
  created() {
    console.log('-- created --');
    this.resultWordingP = '結果';
    // DOM not ready
  },
  mounted() {
    console.log('-- mounted --');
    this.init();
    // document.ready()
  },
  destroyed() {
    console.log('-- destoryed --');
  },
  watch: {
    a1: (value) => {
      console.log(`watch => ${value}`);
    },
  },
  computed: {
    resultWordingP: {
      // get
      get() {
        return this.resultWording;
      },
      // set
      set(value) {
        this.resultWording = `${value} => `;
      },
    },
  },
};
</script>

