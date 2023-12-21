<template>
  <BaseLayout>
    <!-- dynamic input of transaction name, nominal input, type "debit, credit" select -->
    <div class="create-closing">
      <h1>Create Closing</h1>
      <form action="">
        <div class="input-group">
          <label for="date">Date</label>
          <input type="date" id="date" name="date" v-model="submission.date" />
        </div>
        <!-- loop input for transaction name, nominal, note, debit/credit select using table -->
        <!-- using table -->
        <div class="table-wrapper">
          <table>
            <thead>
              <tr>
                <th>Name</th>
                <th>Nominal</th>
                <th>Type</th>
                <th>Note</th>
                <th></th>
              </tr>
            </thead>
            <tbody>
              <!-- loop through the data and display it in the table -->
              <tr
                v-for="(transaction, index) in submission.transactions"
                :key="index"
              >
                <td>
                  <select
                    :class="`item ${
                      transaction.name === '_create' ? 'mb-1' : ''
                    }`"
                    v-model="transaction.name"
                  >
                    <option value="">Select one</option>
                    <option value="_create">+ Create New</option>
                  </select>

                  <input
                    v-show="transaction.name === '_create'"
                    type="text"
                    class="item"
                    v-model="transaction.new_name"
                  />
                </td>
                <td>
                  <input
                    type="number"
                    class="item"
                    v-model="transaction.nominal"
                  />
                </td>
                <td>
                  <select v-model="transaction.type" class="item">
                    <option value="debit">Debit</option>
                    <option value="credit">Credit</option>
                  </select>
                </td>
                <td>
                  <input type="text" v-model="transaction.note" class="item" />
                </td>
                <td>
                  <button
                    type="button"
                    class="utility"
                    @click="() => removeTransaction(index)"
                  >
                    Delete
                  </button>
                </td>
              </tr>
            </tbody>
          </table>
        </div>

        <div class="mb-4">
          <button type="button" @click="addTransaction" class="utility">
            Add Transaction
          </button>
        </div>

        <div class="input-group">
          <button type="submit" @click="handleSubmit">Create Closing</button>
        </div>
      </form>
    </div>
  </BaseLayout>
</template>

<style scoped>
.table-wrapper {
  overflow-x: auto;
  margin-bottom: 1rem;
}

.mb-4 {
  margin-bottom: 1rem;
}

button.utility {
  padding: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 4px;
  background-color: #ccc;
  cursor: pointer;
  color: #000;
  text-decoration: none;
}
</style>

<script setup lang="ts">
import { ref } from "vue";
import BaseLayout from "../../layouts/BaseLayout.vue";

const submission = ref({
  date: new Date().toISOString().slice(0, 10),
  transactions: [
    {
      name: "",
      new_name: "",
      nominal: 0,
      note: "",
      type: "debit",
    },
  ],
});

const addTransaction = () => {
  submission.value.transactions.push({
    name: "",
    new_name: "",
    nominal: 0,
    note: "",
    type: "debit",
  });
};

const removeTransaction = (index: number) => {
  submission.value.transactions.splice(index, 1);
};

const handleSubmit = (event: MouseEvent) => {
  event.preventDefault();
  console.log("submission", submission.value);
  alert("Create Closing");
};
</script>
