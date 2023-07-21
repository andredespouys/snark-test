<template>
  <div style="margin-top: 3rem;">
  <h2 style="text-align: center; font-size: 2rem; font-weight: 500;">2 - Analyze Commands</h2>
  <div>
    <table>
      <tr>
        <th>Product</th>
        <th>Quantity</th>
      </tr>
      <tr>
        <td>refA</td>
        <td class="refAValue">{{ refs.refA }}</td>
      </tr>
      <tr>
        <td>refB</td>
        <td class="refBValue">{{ refs.refB }}</td>
      </tr>
    </table>
    <button @click="analyzeCommands">Analyze Commands</button>
  </div>
</div>
</template>

<script>
export default {
  data() {
    return {
      commands: [
        {
          _id: "1",
          date: 1234566789900,
          totalPrice: 475,
          products: {
            refA: 3,
            refB: 5,
          },
        },
        {
          _id: "1",
          date: 1234566789900,
          totalPrice: 475,
          products: {
            refB: 4,
          },
        },
      ],
      products: [
        {
          ref: "refA",
          name: "A",
          price: 75,
        },
        {
          ref: "refB",
          name: "B",
          price: 50,
        },
      ],
      refs: {
        refA: 0,
        refB: 0,
      },
    };
  },
  methods: {
    analyzeCommands() {
      this.refs.refA = 0;
      this.refs.refB = 0;

      this.commands.forEach((command) => {
        var commandProducts = command.products;
        Object.keys(commandProducts).forEach((product) => {
          if (product === "refA") {
            this.refs.refA += commandProducts[product];
          } else {
            this.refs.refB += commandProducts[product];
          }
        });
      });
    },
  },
};
</script>

<style>
/* Table styles */
table {
  border-collapse: collapse;
  width: 100%;
  max-width: 400px;
  margin: 20px auto;
}

td,
th {
  border: 1px solid #ddd;
  padding: 8px;
  text-align: center;
}

th {
  background-color: #f2f2f2;
}

/* Button styles */
button {
  display: block;
  margin: 20px auto;
  padding: 10px 20px;
  font-size: 16px;
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

/* Flex container for centering */
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
</style>
