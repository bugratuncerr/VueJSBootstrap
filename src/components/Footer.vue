<template>
  <div>
    <b-row class="buttons">
      <b-button size="lg" type="reset" pill variant="primary">Clear</b-button>
      <b-button size="lg" type="submit" pill variant="success"
        >Calculate</b-button
      >
    </b-row>
    <hr style="height:0px;border:none;color:#000;background-color:#333;" />
    <b-row class="dedicated" horizantal="md">
      <medium class="b-form-text">
        <b>Seq</b>
      </medium>
      <medium class="b-form-text">
        <b>Payment Date</b>
      </medium>
      <medium class="b-form-text">
        <b>Installment Amount</b>
      </medium>

      <medium class="b-form-text">
        <b>Principal Amount</b>
      </medium>

      <medium class="b-form-text">
        <b>Interest Amount</b>
      </medium>
      <medium class="b-form-text">
        <b>Tax1 Amount</b>
      </medium>

      <medium class="b-form-text">
        <b>Tax2 Amount</b>
      </medium>

      <medium class="b-form-text">
        <b>Remaining Principal</b>
      </medium>
    </b-row>
    <b-card class="mt-3">
      <pre class="m-0">{{ form }}</pre>
    </b-card>
  </div>
</template>

<script>
export default {};
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
