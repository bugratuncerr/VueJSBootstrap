<template>
  <div>
    <b-form @submit="onSubmit" @reset="onReset" v-if="show">
      <b-row>
        <b-col cols="4">
          <b-form-group
            id="input-group-1"
            label="Resolving/Fixed Expiry:"
            label-for="input-1"
          >
            <b-form-select
              id="input-1"
              v-model="form.limitType"
              :options="limitTypes"
              required
            ></b-form-select>
          </b-form-group>
        </b-col>
        <b-col cols="4">
          <b-form-group id="input-group-1" label="Product:" label-for="input-2">
            <b-form-select
              id="input-2"
              v-model="form.product"
              :options="products"
              required
            ></b-form-select>
          </b-form-group>
        </b-col>

        <b-col cols="3">
          <b-form-group id="input-group-1" label="Amount:" label-for="input-3">
            <b-form-input
              id="input-3"
              v-model="form.amount"
              required
              type="number"
              min="0"
              step="0.001"
            ></b-form-input>
          </b-form-group>
        </b-col>
        <b-col cols="1">
          <b-form-group
            id="input-group-1"
            label="Currency:"
            label-for="input-4"
          >
            <b-form-select
              id="input-4"
              v-model="form.currency"
              :options="currencies"
              required
            ></b-form-select>
          </b-form-group>
        </b-col>
      </b-row>
      <b-row>
        <b-col cols="4">
          <b-form-group
            id="input-group-2"
            label="Total Interest:"
            label-for="input-1"
          >
            <b-form-input
              id="input-1"
              v-model="form.totalInterest"
              required
              type="number"
              min="0"
              step="0.01"
            ></b-form-input>
          </b-form-group>
        </b-col>
        <b-col>
          <b-form-group
            id="input-group-2"
            label="First Repayment Date:"
            label-for="input-2"
          >
            <div class="input-group-prepend">
              <span class="input-group-text" id="basic-addon1">&#128197;</span>
              <date-picker v-model="form.date" :config="options"></date-picker>
            </div>
          </b-form-group>
        </b-col>
        <b-col cols="4">
          <b-form-group
            id="input-group-2"
            label="Number of installments:"
            label-for="input-3"
          >
            <b-form-input
              id="input-3"
              v-model="form.noInstallment"
              required
              min="0"
              type="number"
            ></b-form-input>
          </b-form-group>
        </b-col>
      </b-row>
      <b-row>
        <b-col cols="4">
          <b-form-group id="input-group-3" label="Tax1:" label-for="input-1">
            <div class="input-group-prepend">
              <span class="input-group-text" id="basic-addon1">%</span>
              <b-form-input
                id="input-3"
                v-model="form.tax1"
                required
                min="0"
                step="0.01"
                type="number"
              ></b-form-input>
            </div>
          </b-form-group>
        </b-col>
        <b-col cols="4">
          <b-form-group id="input-group-3" label="Tax2:" label-for="input-2">
            <div class="input-group-prepend">
              <span class="input-group-text" id="basic-addon1">%</span>
              <b-form-input
                id="input-3"
                v-model="form.tax2"
                required
                min="0"
                step="0.01"
                type="number"
              ></b-form-input>
            </div>
          </b-form-group>
        </b-col>
        <b-col cols="4">
          <b-form-group id="input-group-3" label="Fee:" label-for="input-3">
            <div class="input-group-prepend">
              <span class="input-group-text" id="basic-addon1">$</span>
              <b-form-input
                id="input-3"
                v-model="form.fee"
                required
                min="0"
                step="0.01"
                type="number"
              ></b-form-input>
            </div>
          </b-form-group>
        </b-col>
      </b-row>
      <b-row class="justify-content-md-center">
        <b-form-group>
          <b-form-radio-group
            id="radio-group-1"
            v-model="selected"
            :options="radioOptions"
            name="radio-options-slots"
            style="height: 50px;padding-top: 10px;font-size: large; border:2px solid black; border-radius:20px;"
          ></b-form-radio-group>
        </b-form-group>
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
