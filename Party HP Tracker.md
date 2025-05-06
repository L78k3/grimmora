## Gage Greenpather
**Current HP**: <span id="gage-current-hp">33</span>/<span id="gage-max-hp">33</span>

```button
name Take Damage
type command
action Damage Gage
color red
```

```button
name Heal
type command
action Heal Gage
color green
```

```button
name Reset HP
type command
action Reset Gage HP
color blue
```

## Other Party Member
**Current HP**: <span id="other-current-hp">25</span>/<span id="other-max-hp">25</span>

```button
name Take Damage
type command
action Damage Other
color red
```

```button
name Heal
type command
action Heal Other
color green
```

```button
name Reset HP
type command
action Reset Other HP
color blue
```

## JS Code (Hidden Section)

```js
// Gage HP Functions
function damageGage() {
  // Get current HP value
  const currentHpSpan = document.getElementById('gage-current-hp');
  let currentHp = parseInt(currentHpSpan.textContent);
  
  // Prompt for damage amount
  const damage = parseInt(prompt("Enter damage amount:", "0"));
  
  // Calculate new HP (ensuring it doesn't go below 0)
  if (!isNaN(damage) && damage > 0) {
    currentHp = Math.max(0, currentHp - damage);
    currentHpSpan.textContent = currentHp;
    
    // Optional: Add to session log
    const timestamp = new Date().toLocaleTimeString();
    const logEntry = `${timestamp} - Gage took ${damage} damage. HP now ${currentHp}/${document.getElementById('gage-max-hp').textContent}\n`;
    appendToSessionLog(logEntry);
  }
}

function healGage() {
  // Get current HP value and max HP
  const currentHpSpan = document.getElementById('gage-current-hp');
  const maxHpSpan = document.getElementById('gage-max-hp');
  let currentHp = parseInt(currentHpSpan.textContent);
  const maxHp = parseInt(maxHpSpan.textContent);
  
  // Prompt for healing amount
  const healing = parseInt(prompt("Enter healing amount:", "0"));
  
  // Calculate new HP (ensuring it doesn't go over max)
  if (!isNaN(healing) && healing > 0) {
    currentHp = Math.min(maxHp, currentHp + healing);
    currentHpSpan.textContent = currentHp;
    
    // Optional: Add to session log
    const timestamp = new Date().toLocaleTimeString();
    const logEntry = `${timestamp} - Gage healed ${healing} HP. HP now ${currentHp}/${maxHp}\n`;
    appendToSessionLog(logEntry);
  }
}

function resetGageHp() {
  // Reset to max HP
  const currentHpSpan = document.getElementById('gage-current-hp');
  const maxHpSpan = document.getElementById('gage-max-hp');
  const maxHp = parseInt(maxHpSpan.textContent);
  
  currentHpSpan.textContent = maxHp;
  
  // Optional: Add to session log
  const timestamp = new Date().toLocaleTimeString();
  const logEntry = `${timestamp} - Gage's HP reset to full (${maxHp})\n`;
  appendToSessionLog(logEntry);
}

// Other Character HP Functions
function damageOther() {
  // Similar code as damageGage but for other character
  const currentHpSpan = document.getElementById('other-current-hp');
  let currentHp = parseInt(currentHpSpan.textContent);
  
  const damage = parseInt(prompt("Enter damage amount:", "0"));
  
  if (!isNaN(damage) && damage > 0) {
    currentHp = Math.max(0, currentHp - damage);
    currentHpSpan.textContent = currentHp;
    
    const timestamp = new Date().toLocaleTimeString();
    const logEntry = `${timestamp} - Party member took ${damage} damage. HP now ${currentHp}/${document.getElementById('other-max-hp').textContent}\n`;
    appendToSessionLog(logEntry);
  }
}

function healOther() {
  // Similar code as healGage but for other character
  const currentHpSpan = document.getElementById('other-current-hp');
  const maxHpSpan = document.getElementById('other-max-hp');
  let currentHp = parseInt(currentHpSpan.textContent);
  const maxHp = parseInt(maxHpSpan.textContent);
  
  const healing = parseInt(prompt("Enter healing amount:", "0"));
  
  if (!isNaN(healing) && healing > 0) {
    currentHp = Math.min(maxHp, currentHp + healing);
    currentHpSpan.textContent = currentHp;
    
    const timestamp = new Date().toLocaleTimeString();
    const logEntry = `${timestamp} - Party member healed ${healing} HP. HP now ${currentHp}/${maxHp}\n`;
    appendToSessionLog(logEntry);
  }
}

function resetOtherHp() {
  const currentHpSpan = document.getElementById('other-current-hp');
  const maxHpSpan = document.getElementById('other-max-hp');
  const maxHp = parseInt(maxHpSpan.textContent);
  
  currentHpSpan.textContent = maxHp;
  
  const timestamp = new Date().toLocaleTimeString();
  const logEntry = `${timestamp} - Party member's HP reset to full (${maxHp})\n`;
  appendToSessionLog(logEntry);
}

// Helper function to log HP changes
function appendToSessionLog(logEntry) {
  // You can modify this to append to a specific section or file
  console.log(logEntry);
  // For advanced usage: Use Obsidian API to write to a session log file
}

// Register custom commands
app.commands.addCommand({
  id: 'damage-gage',
  name: 'Damage Gage',
  callback: () => damageGage()
});

app.commands.addCommand({
  id: 'heal-gage',
  name: 'Heal Gage',
  callback: () => healGage()
});

app.commands.addCommand({
  id: 'reset-gage-hp',
  name: 'Reset Gage HP',
  callback: () => resetGageHp()
});

app.commands.addCommand({
  id: 'damage-other',
  name: 'Damage Other',
  callback: () => damageOther()
});

app.commands.addCommand({
  id: 'heal-other',
  name: 'Heal Other',
  callback: () => healOther()
});

app.commands.addCommand({
  id: 'reset-other-hp',
  name: 'Reset Other HP',
  callback: () => resetOtherHp()
});
```

## HP Change Log
<!-- HP changes will be logged here -->