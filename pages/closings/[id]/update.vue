<template>
  <BaseLayout>
    <!-- dynamic input of transaction name, nominal input, type "debit, credit" select -->
    <div class="update-closing">
      <h1>Update Closing</h1>
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
                  <input type="hidden" name="id" v-model="transaction.id" />
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
          <button type="submit" @click="handleSubmit">Update Closing</button>
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
import BaseLayout from "../../../layouts/BaseLayout.vue";
import { useRouter } from "vue-router";

const initial = {
  date: "2021-01-01",
  transactions: [
    {
      id: "2fbfc891-1ad5-4963-8f8f-2d87142c73b5",
      name: "2021-01-01",
      type: "debit",
      nominal: 100000,
      note: "test",
    },
    {
      id: "2fbfc891-1ad5-4963-8f8f-2d87142c73b5",
      name: "2021-01-01",
      type: "debit",
      nominal: 100000,
      note: "test",
    },
    {
      id: "2fbfc891-1ad5-4963-8f8f-2d87142c73b5",
      name: "2021-01-01",
      type: "debit",
      nominal: 100000,
      note: "test",
    },
    {
      id: "2fbfc891-1ad5-4963-8f8f-2d87142c73b5",
      name: "2021-01-01",
      type: "debit",
      nominal: 100000,
      note: "test",
    },
    {
      id: "2fbfc891-1ad5-4963-8f8f-2d87142c73b5",
      name: "2021-01-01",
      type: "debit",
      nominal: 100000,
      note: "test",
    },
    {
      id: "2fbfc891-1ad5-4963-8f8f-2d87142c73b5",
      name: "2021-01-01",
      type: "debit",
      nominal: 100000,
      note: "test",
    },
  ],
};

const submission = ref({
  ...initial,
  transactions: initial.transactions.map((item) => ({ ...item, new_name: "" })),
});

const addTransaction = () => {
  submission.value.transactions.push({
    id: "",
    name: "",
    new_name: "",
    nominal: 0,
    note: "",
    type: "debit",
  });
};

const { back } = useRouter();

const removeTransaction = (index: number) => {
  submission.value.transactions.splice(index, 1);
};

const handleSubmit = (event: MouseEvent) => {
  event.preventDefault();
  console.log("submission", submission.value);
  back();
  alert("Create Closing");
};
</script>
