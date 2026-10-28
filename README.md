
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>GPU Power Share</title>

  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      padding: 20px;
      font-family: Arial, sans-serif;
      background: #f0f4f8;
      color: #1f2937;
    }

    .container {
      max-width: 850px;
      margin: auto;
    }

    h1 {
      text-align: center;
      color: #174ea6;
    }

    .subtitle {
      text-align: center;
      color: #64748b;
    }

    .card {
      background: white;
      padding: 20px;
      margin: 18px 0;
      border-radius: 12px;
      box-shadow: 0 3px 12px #00000012;
    }

    .device {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
      padding: 14px;
      margin: 10px 0;
      border: 1px solid #e2e8f0;
      border-radius: 8px;
    }

    .note {
      color: #64748b;
      font-size: 14px;
      margin: 6px 0 0;
    }

    .status {
      padding: 6px 10px;
      border-radius: 20px;
      font-size: 13px;
      font-weight: bold;
      white-space: nowrap;
    }

    .online {
      color: #166534;
      background: #dcfce7;
    }

    .offline {
      color: #991b1b;
      background: #fee2e2;
    }

    .registered {
      color: #1d4ed8;
      background: #dbeafe;
    }

    .number {
      font-size: 36px;
      font-weight: bold;
      color: #174ea6;
    }

    label {
      display: block;
      margin-top: 14px;
      margin-bottom: 6px;
      font-weight: bold;
    }

    input, select {
      width: 100%;
      padding: 11px;
      border: 1px solid #cbd5e1;
      border-radius: 7px;
      font-size: 16px;
      background: white;
    }

    button {
      padding: 11px 14px;
      margin: 8px 6px 0 0;
      border: none;
      border-radius: 7px;
      background: #174ea6;
      color: white;
      font-size: 14px;
      cursor: pointer;
    }

    button:hover {
      background: #123b80;
    }

    .result {
      margin-top: 14px;
      font-weight: bold;
      overflow-wrap: anywhere;
    }

    @media (max-width: 500px) {
      body {
        padding: 10px;
      }

      .card {
        padding: 15px;
      }

      .device {
        align-items: flex-start;
      }
    }
  </style>
</head>

<body>
  <div class="container">

    <h1>GPU Power Share</h1>
    <p class="subtitle">
      A demonstration dashboard for sharing GPU computing power
    </p>

    <div class="card">
      <h2>Dashboard Overview</h2>
      <p>Computers currently online:</p>
      <div class="number" id="gpuCount">1</div>
      <p class="note">
        This number includes the two sample computers only when online.
      </p>
    </div>

    <div class="card">
      <h2>Computer Status</h2>
      <p class="note">
        Practice mode: these are sample computers, not real connections.
      </p>

      <div class="device">
        <div>
          <strong>Computer 1</strong>
          <p class="note">RTX 3060</p>
        </div>
        <span id="status1" class="status online">Online</span>
      </div>

      <div class="device">
        <div>
          <strong>Computer 2</strong>
          <p class="note">RTX 4090</p>
        </div>
        <span id="status2" class="status offline">Offline</span>
      </div>

      <button onclick="toggleComputer(1)">
        Change Computer 1 Status
      </button>

      <button onclick="toggleComputer(2)">
        Change Computer 2 Status
      </button>

      <h3>Registered Computers</h3>
      <div id="registeredComputers"></div>
    </div>

    <div class="card">
      <h2>Earnings Calculator</h2>

      <label for="gpu">Choose a GPU</label>
      <select id="gpu">
        <option value="0">Choose a model</option>
        <option value="10">RTX 3060 — example ₹10/hour</option>
        <option value="25">RTX 4090 — example ₹25/hour</option>
      </select>

      <label for="hours">Hours used per day (1–24)</label>
      <input
        id="hours"
        type="number"
        min="1"
        max="24"
        value="8"
      >

      <button onclick="calculateEarnings()">
        Calculate Example Earnings
      </button>

      <p id="earningsResult" class="result"></p>

      <p class="note">
        These rates are examples only, not actual earnings or a promise
        of payment.
      </p>
    </div>

    <div class="card">
      <h2>Register a Computer</h2>

      <label for="computerName">Computer Name</label>
      <input
        type="text"
        id="computerName"
        placeholder="Enter computer name"
      >

      <label for="gpuModel">GPU Model</label>
      <select id="gpuModel">
        <option value="RTX 3060">RTX 3060</option>
        <option value="RTX 4090">RTX 4090</option>
        <option value="Other GPU">Other GPU</option>
      </select>

      <button onclick="registerComputer()">
        Register Computer
      </button>

      <p id="registrationMessage" class="result"></p>
    </div>

    <p class="subtitle">
      Demonstration only — no real GPU sharing or payments are connected.
    </p>

  </div>

  <script>
    let firstOnline = true;
    let secondOnline = false;

    function toggleComputer(number) {
      if (number === 1) {
        firstOnline = !firstOnline;
      } else if (number === 2) {
        secondOnline = !secondOnline;
      }

      updateComputerStatus();
    }

    function updateComputerStatus() {
      const first = document.getElementById("status1");
      const second = document.getElementById("status2");

      first.textContent = firstOnline ? "Online" : "Offline";
      first.className = "status " +
        (firstOnline ? "online" : "offline");

      second.textContent = secondOnline ? "Online" : "Offline";
      second.className = "status " +
        (secondOnline ? "online" : "offline");

      const onlineCount =
        Number(firstOnline) + Number(secondOnline);

      document.getElementById("gpuCount").textContent = onlineCount;
    }

    function calculateEarnings() {
      const rate = Number(document.getElementById("gpu").value);
      const hours = Number(document.getElementById("hours").value);
      const result = document.getElementById("earningsResult");

      if (rate <= 0) {
        result.textContent = "Please choose a GPU model.";
        return;
      }

      if (!Number.isFinite(hours) || hours < 1 || hours > 24) {
        result.textContent = "Please enter between 1 and 24 hours.";
        return;
      }

      const daily = rate * hours;
      const monthly = daily * 30;

      result.textContent =
        "Example: ₹" + daily + " per day, or ₹" +
        monthly + " for 30 days.";
    }

    function registerComputer() {
      
function registerComputer() {
  const name = document.getElementById("computerName").value.trim();
  const gpu = document.getElementById("gpuModel").value;
  const message = document.getElementById("registrationMessage");

  if (name === "") {
    message.textContent = "Please enter a computer name.";
    return;
  }

  const computers = JSON.parse(
    localStorage.getItem("registeredComputers") || "[]"
  );

  computers.push({ name: name, gpu: gpu });

  localStorage.setItem(
    "registeredComputers",
    JSON.stringify(computers)
  );

  document.getElementById("computerName").value = "";

  message.textContent = name + " registered successfully!";

  displayRegisteredComputers();
}

function displayRegisteredComputers() {
  const list = document.getElementById("registeredComputers");

  list.replaceChildren();

  const computers = JSON.parse(
    localStorage.getItem("registeredComputers") || "[]"
  );

  computers.forEach(function(computer) {
    const device = document.createElement("div");
    device.className = "device";

    const details = document.createElement("div");

    const computerName = document.createElement("strong");
    computerName.textContent = computer.name;

    const gpuName = document.createElement("p");
    gpuName.className = "note";
    gpuName.textContent = computer.gpu;

    const status = document.createElement("span");
    status.className = "status registered";
    status.textContent = "Registered";

    details.appendChild(computerName);
    details.appendChild(gpuName);
    device.appendChild(details);
    device.appendChild(status);

    list.appendChild(device);
  });
}

displayRegisteredComputers();


      const device = document.createElement("div");
      device.className = "device";

      const details = document.createElement("div");

      const computerName = document.createElement("strong");
      computerName.textContent = name;

      const gpuName = document.createElement("p");
      gpuName.className = "note";
      gpuName.textContent = gpu;

      const status = document.createElement("span");
      status.className = "status registered";
      status.textContent = "Registered";

      details.appendChild(computerName);
      details.appendChild(gpuName);

      device.appendChild(details);
      device.appendChild(status);

      list.appendChild(device);

      message.textContent = name + " registered successfully!";
      document.getElementById("computerName").value = "";
    }
  </script>

</body>
</html>

</html>
