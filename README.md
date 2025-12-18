<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Asset Liability Calculator</title>

<style>
body {
  font-family: Arial, sans-serif;
  background: #e5e7eb;
  display: flex;
  justify-content: center;
  padding: 20px;
}

.container {
  width: 100%;
  max-width: 380px;
  background: white;
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 10px 25px rgba(0,0,0,0.15);
}

.section-title {
  text-align: center;
  padding: 10px;
  font-weight: bold;
}

.assets { background: #dbeafe; }
.liabilities { background: #fee2e2; }

.row {
  display: flex;
  gap: 5px;
  padding: 6px;
}

.row input {
  flex: 1;
  padding: 6px;
}

button {
  width: 100%;
  padding: 10px;
  margin: 6px 0;
  font-size: 16px;
  cursor: pointer;
}

.calculate {
  background: #ef4444;
  color: white;
  border: none;
}

.result {
  background: #1f2933;
  color: white;
  padding: 15px;
  text-align: center;
  font-size: 18px;
}
</style>
</head>

<body>

<div class="container">

  <!-- ASSETS -->
  <div class="section-title assets">Assets</div>
  <div id="assets"></div>
  <button onclick="addAsset()">➕ Add Asset</button>

  <!-- LIABILITIES -->
  <div class="section-title liabilities">Liabilities</div>
  <div id="liabilities"></div>
  <button onclick="addLiability()">➕ Add Liability</button>

  <button class="calculate" onclick="calculate()">CALCULATE</button>

  <div class="result">
    Net Worth = ₹ <span id="net">0</span>
  </div>

</div>

<script>
function addAsset() {
  document.getElementById("assets").innerHTML += `
    <div class="row">
      <input placeholder="Item">
      <input type="number" placeholder="Amount">
    </div>`;
}

function addLiability() {
  document.getElementById("liabilities").innerHTML += `
    <div class="row">
      <input placeholder="Item">
      <input type="number" placeholder="Amount">
    </div>`;
}

function calculate() {
  let totalAssets = 0;
  let totalLiabilities = 0;

  document.querySelectorAll("#assets input[type='number']")
    .forEach(i => totalAssets += Number(i.value || 0));

  document.querySelectorAll("#liabilities input[type='number']")
    .forEach(i => totalLiabilities += Number(i.value || 0));

  document.getElementById("net").innerText =
    totalAssets - totalLiabilities;
}

// default rows
addAsset();
addLiability();
</script>

</body>
</html>
