<template>
<div>
  <nav class="navbar navbar-expand-lg navbar-light bg-light ">
   <h1 class= "track"> Adisa <br />Expenses Tracker </h1>

   <!-- Button trigger modal -->
    <button type="button" class="btn btn-primary" data-toggle="modal" data-target="#exampleModalCenter">
      New Expense
    </button>
      <div style="float: right; margin-left: 80px;">
        <p style= "font-size: 20px;"><b>Total is:</b> {{ totalExpense }}</p>
      </div>
    <!-- Modal -->
    <div class="modal fade" id="exampleModalCenter" tabindex="-1" role="dialog" aria-labelledby="exampleModalCenterTitle" aria-hidden="true">
      <div class="modal-dialog modal-dialog-centered" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalCenterTitle">Input Expense</h5>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">
           <form>
              <div class="form-group">
                <label for="formGroupExampleInput">Item</label>
                <input v-model="expense.itemInput" type="text" class="form-control" id="formGroupExampleInput" placeholder="Item...">
              </div>
              <div class="form-group">
                <label for="formGroupExampleInput2">Amount</label>
                <input v-model="expense.amountInput" type="number" class="form-control" id="formGroupExampleInput2" placeholder="Amount...">
              </div>
              <div class="form-group">
                <label for="formGroupExampleInput">Details</label>
                <input v-model="expense.detailsInput" type="text" class="form-control" id="formGroupExampleInput" placeholder="Details...">
              </div>
            </form>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
            <button type="button" class="btn btn-primary" @click="saveChanges">Save</button>
          </div>
        </div>
      </div>
    </div>
  </nav>
</div>
</template>

<script>
export default {
props: ["expense", "totalExpense"],
  data() {
    return {

      };
  },
  methods: {
    saveChanges() {
      const item = {
        "tell": this.expense.itemInput,
        "amount": this.expense.amountInput,
        "details": this.expense.detailsInput
      };
      this.$emit("update-home", item);
      this.expense.itemInput = "";
      this.expense.amountInput = "";
      this.expense.detailsInput = "";
    },
  }
}
</script>

<style>
.track {
  font-size: 18px;
  font-type: bold;
}
.btn {
  margin-left: 70px;
  background: green;
}
.btn:hover{
  background: linear-gradient(45deg, rgb(98, 31, 155) 0%, rgb(98, 31, 155) 24%,rgb(90, 59, 158) 24%, rgb(90, 59, 158) 25%,rgb(82, 86, 161) 25%, rgb(82, 86, 161) 27%,rgb(74, 114, 164) 27%, rgb(74, 114, 164) 36%,rgb(66, 141, 167) 36%, rgb(66, 141, 167) 73%,rgb(58, 169, 170) 73%, rgb(58, 169, 170) 75%,rgb(50, 196, 173) 75%, rgb(50, 196, 173) 80%,rgb(42, 224, 176) 80%, rgb(42, 224, 176) 100%);
}
</style>