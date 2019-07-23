<template>
  <div>
    <b-form @submit="onSubmit" @reset="onReset" v-if="show">
      <b-row>
        <b-col cols="4">
          <b-form-group
            id="input-group-4"
            label="Calculation Type:"
            label-for="input-1"
          >
            <b-form-select
              id="input-1"
              v-model="form.calculationType"
              :options="calculationTypes"
              required
            ></b-form-select>
          </b-form-group>
        </b-col>
      </b-row>
      <b-row>
        <b-col cols="4">
          <b-form-group
            id="input-group-5"
            label="Principal Repayment Frq:"
            label-for="input-1"
          >
            <b-form-select
              id="input-1"
              v-model="form.principalRepaymentFrq"
              :options="principalRepaymentFrqs"
              required
            ></b-form-select>
          </b-form-group>
        </b-col>
        <b-col cols="4">
          <b-form-group id="input-group-5" label="Day:" label-for="input-2">
            <b-form-input
              id="input-2"
              v-model="form.day"
              required
              type="number"
              min="0"
            ></b-form-input>
          </b-form-group>
        </b-col>
        <b-col class="lol" cols="4">
          <b-form-group>
            <b-form-radio-group
              id="radio-group-2"
              v-model="selected2"
              :options="radioOptions2"
              name="radio-options"
              style="padding-left: 60px;"
            ></b-form-radio-group>
          </b-form-group>
        </b-col>
      </b-row>
      <b-row>
        <b-col cols="4">
          <b-form-group
            id="input-group-6"
            label="Interest Repayment Frq:"
            label-for="input-1"
          >
            <b-form-select
              id="input-1"
              v-model="form.interestRepaymentFrq"
              :options="interestRepaymentFrqs"
              required
            ></b-form-select>
          </b-form-group>
        </b-col>
        <b-col cols="4">
          <b-form-group id="input-group-6" label="Day:" label-for="input-2">
            <b-form-input
              id="input-2"
              v-model="form.day2"
              required
              type="number"
              min="0"
            ></b-form-input>
          </b-form-group>
        </b-col>
        <b-col class="lol" cols="4">
          <b-form-group>
            <b-form-radio-group
              id="radio-group-3"
              v-model="selected3"
              :options="radioOptions3"
              name="radio-inline"
              style="padding-left: 60px;"
            ></b-form-radio-group>
          </b-form-group>
        </b-col>
      </b-row>
    </b-form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      options: {
        format: "DD/MM/YYYY",
        useCurrent: false
      },
      form: {
        amount: "",
        date: "",
        noInstallment: "",
        totalInterest: "",
        limitType: "null",
        product: "null",
        currency: "null",
        calculationType: "null",
        tax1: "",
        tax2: "",
        fee: "",
        day: "",
        day2: "",
        selected: "",
        selected2: "",
        selected3: "",
        principalRepaymentFrq: "null",
        interestRepaymentFrq: "null"
      },

      radioOptions: [
        { text: "Equal Payment", value: "Equal Payment" },
        { text: "No Payment Period      ", value: "No Payment Period      " },
        { text: "Balloon Payment", value: "Balloon Payment" },
        {
          text: "Increase/Decrease Payment",
          value: "Increase/Decrease Payment"
        },
        { text: "Flexible Payment", value: "Flexible Payment" }
      ],
      radioOptions2: [
        { text: "Next Business Day", value: "Next Business Day" },
        { text: "Previous Business Day", value: "Previous Business Day" }
      ],
      radioOptions3: [
        { text: "Next Business Day", value: "Next Business Day" },
        { text: "Previous Business Day", value: "Previous Business Day" }
      ],
      interestRepaymentFrqs: ["Monthly", "Quarterly", "Be", "Replaced"],
      principalRepaymentFrqs: ["Monthly", "Quarterly", "Be", "Replaced"],
      products: ["CLE - Commercial Loan", "Will", "Be", "Replaced"],
      currencies: ["USD", "TRY", "EUR", "Will", "Be", "Replaced"],
      limitTypes: ["Fixed", "Not Fixed", "Blah"],
      calculationTypes: ["Principal Increase", "Will", "Be", "Replaced"],
      show: true
    };
  },
  methods: {
    onSubmit(evt) {
      evt.preventDefault();
      alert(JSON.stringify(this.form));
    },
    onReset(evt) {
      evt.preventDefault();
      // Reset our form values
      this.limitType = null;
      this.product = null;
      this.amount = "";
      this.currency = null;
      this.totalInterest = "";
      this.date = "";
      this.noInstallment = "";
      this.tax1 = "";
      this.tax2 = "";
      this.fee = "";
      this.selected = "";
      this.calculationType = null;
      this.principalRepaymentFrq = null;
      this.day = "";
      this.selected2 = "";
      this.interestRepaymentFrq = null;
      this.day2 = "";
      this.selected3 = "";
      // Trick to reset/clear native browser form validation state
      this.show = false;
      this.$nextTick(() => {
        this.show = true;
      });
    }
  }
};
</script>

<style>
div {
  padding-right: 5px;
  padding-left: 5px;
}
.lol {
  padding-top: 35px;
}
.dedicated {
  justify-content: space-between;
  background-color: rgb(168, 235, 247);

  padding-left: 20px;

  height: 60px;

  width: auto;

  padding-top: 17px;
  border: 2px solid black;
}

.buttons {
  justify-content: flex-end;
}
.justify-content-md-center {
  padding-top: 15px;
}
.navbar {
  padding: 0px !important;
  padding-top: 10px !important;
  padding-left: 20px !important;
  margin: 0px !important;
}
</style>
