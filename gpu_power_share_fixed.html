<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>GPU Power Share</title>
  <style>
    * { box-sizing: border-box; }
    body { margin: 0; padding: 20px; font-family: Arial, sans-serif; background: #f0f4f8; color: #1f2937; }
    .container { max-width: 850px; margin: auto; }
    h1 { text-align: center; color: #174ea6; }
    .subtitle { text-align: center; color: #64748b; }
    .card { background: white; padding: 20px; margin: 18px 0; border-radius: 12px; box-shadow: 0 3px 12px #00000012; }
    .device { display: flex; align-items: center; justify-content: space-between; gap: 12px; padding: 14px; margin: 10px 0; border: 1px solid #e2e8f0; border-radius: 8px; }
    .note { color: #64748b; font-size: 14px; margin: 6px 0 0; }
    .status { padding: 6px 10px; border-radius: 20px; font-size: 13px; font-weight: bold; white-space: nowrap; }
    .online { color: #166534; background: #dcfce7; }
    .offline { color: #991b1b; background: #fee2e2; }
    .registered { color: #1d4ed8; background: #dbeafe; }
    .number { font-size: 36px; font-weight: bold; color: #174ea6; }
    label { display: block; margin-top: 14px; margin-bottom: 6px; font-weight: bold; }
    input, select { width: 100%; padding: 11px; border: 1px solid #cbd5e1; border-radius: 7px; font-size: 16px; background: white; }
    button { padding: 11px 14px; margin: 8px 6px 0 0; border: none; border-radius: 7px; background: #174ea6; color: white; font-size: 14px; cursor: pointer; }
    button:hover { background: #123b80; }
    button.remove { background: #b91c1c; }
    button.remove:hover { background: #991b1b; }
    .result { margin-top: 14px; font-weight: bold; overflow-wrap: anywhere; }
    @media (max-width: 500px) { body { padding: 10px; } .card { padding: 15px; } .device { align-items: flex-start; } }
  </style>
</head>
<body>
  <div class="container">
    <h1>GPU Power Share</h1>
    <p class="subtitle">A demonstration dashboard for sharing GPU computing power</p>

    <div class="card">
      <h2>Dashboard Overview</h2>
      <p>Sample computers currently online:</p>
      <div class="number" id="gpuCount">1</div>
      <p class="note">This count covers the two sample computers only, not registered computers.</p>
    </div>

    <div class="card">
      <h2>Sample Computer Status</h2>
      <p class="note">Practice mode: these are sample computers, not real connections.</p>
      <div class="device">
        <div><strong>Computer 1</strong><p class="note">RTX 3060</p></div>
        <span id="status1" class="status online">Online</span>
      </div>
      <div class="device">
        <div><strong>Computer 2</strong><p class="note">RTX 4090</p></div>
        <span id="status2" class="status offline">Offline</span>
      </div>
      <button type="button" onclick="toggleComputer(1)">Change Computer 1 Status</button>
      <button type="button" onclick="toggleComputer(2)">Change Computer 2 Status</button>

      <h3>Registered Computers</h3>
      <div id="registeredComputers"></div>
      <p id="registeredEmptyMessage" class="note">No computers registered yet.</p>
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
      <input id="hours" type="number" min="1" max="24" value="8">
      <button type="button" onclick="calculateEarnings()">Calculate Example Earnings</button>
      <p id="earningsResult" class="result" aria-live="polite"></p>
      <p class="note">These rates are examples only, not actual earnings or a promise of payment.</p>
    </div>

    <div class="card">
      <h2>Register a Computer</h2>
      <label for="computerName">Computer Name</label>
      <input type="text" id="computerName" maxlength="60" placeholder="Enter computer name">
      <label for="gpuModel">GPU Model</label>
      <select id="gpuModel">
        <option value="RTX 3060">RTX 3060</option>
        <option value="RTX 4090">RTX 4090</option>
        <option value="Other GPU">Other GPU</option>
      </select>
      <button type="button" onclick="registerComputer()">Register Computer</button>
      <p id="registrationMessage" class="result" aria-live="polite"></p>
    </div>

    <p class="subtitle">Demonstration only — no real GPU sharing, remote connections, or payments are connected.</p>
  </div>

  <script>
    let firstOnline = true;
    let secondOnline = false;
    const STORAGE_KEY = "registeredComputers";

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
      first.className = "status " + (firstOnline ? "online" : "offline");
      second.textContent = secondOnline ? "Online" : "Offline";
      second.className = "status " + (secondOnline ? "online" : "offline");

      document.getElementById("gpuCount").textContent =
        Number(firstOnline) + Number(secondOnline);
    }

    function calculateEarnings() {
      const rate = Number(document.getElementById("gpu").value);
      const hoursInput = document.getElementById("hours");
      const hours = Number(hoursInput.value);
      const result = document.getElementById("earningsResult");

      if (rate <= 0) {
        result.textContent = "Please choose a GPU model.";
        return;
      }
      if (hoursInput.value.trim() === "" || !Number.isFinite(hours) || hours < 1 || hours > 24) {
        result.textContent = "Please enter a number of hours from 1 to 24.";
        return;
      }
      const daily = rate * hours;
      const monthly = daily * 30;
      result.textContent = "Example: ₹" + daily + " per day, or ₹" + monthly + " for 30 days.";
    }

    function getRegisteredComputers() {
      try {
        const saved = JSON.parse(localStorage.getItem(STORAGE_KEY) || "[]");
        return Array.isArray(saved) ? saved.filter(function(item) {
          return item && typeof item.name === "string" && typeof item.gpu === "string";
        }) : [];
      } catch (error) {
        return [];
      }
    }

    function saveRegisteredComputers(computers) {
      try {
        localStorage.setItem(STORAGE_KEY, JSON.stringify(computers));
        return true;
      } catch (error) {
        document.getElementById("registrationMessage").textContent =
          "Could not save this computer in the browser. Check browser storage settings.";
        return false;
      }
    }

    function registerComputer() {
      const nameInput = document.getElementById("computerName");
      const name = nameInput.value.trim();
      const gpu = document.getElementById("gpuModel").value;
      const message = document.getElementById("registrationMessage");

      if (!name) {
        message.textContent = "Please enter a computer name.";
        nameInput.focus();
        return;
      }

      const computers = getRegisteredComputers();
      computers.push({ id: Date.now().toString() + Math.random().toString(16).slice(2), name: name, gpu: gpu });

      if (!saveRegisteredComputers(computers)) return;

      nameInput.value = "";
      message.textContent = name + " registered successfully!";
      displayRegisteredComputers();
    }

    function removeComputer(id) {
      const computers = getRegisteredComputers().filter(function(computer) {
        return computer.id !== id;
      });
      if (saveRegisteredComputers(computers)) {
        document.getElementById("registrationMessage").textContent = "Registration removed.";
        displayRegisteredComputers();
      }
    }

    function displayRegisteredComputers() {
      const list = document.getElementById("registeredComputers");
      const emptyMessage = document.getElementById("registeredEmptyMessage");
      list.replaceChildren();

      const computers = getRegisteredComputers();
      emptyMessage.hidden = computers.length > 0;

      computers.forEach(function(computer, index) {
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

        const removeButton = document.createElement("button");
        removeButton.type = "button";
        removeButton.className = "remove";
        removeButton.textContent = "Remove";
        removeButton.setAttribute("aria-label", "Remove " + computer.name);
        removeButton.addEventListener("click", function() {
          removeComputer(computer.id);
        });

        details.appendChild(computerName);
        details.appendChild(gpuName);
        device.appendChild(details);
        device.appendChild(status);
        device.appendChild(removeButton);
        list.appendChild(device);
      });
    }

    updateComputerStatus();
    displayRegisteredComputers();
  </script>
</body>
</html>
