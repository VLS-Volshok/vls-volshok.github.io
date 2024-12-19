# Auto Heal
## Summary
All units in BAR begin repairing themselves one-minute after bezing damaged, generally at the rate of 5 HP/second. Some units (like the Commander) have additional healing that continuously repairs a set value.

## Types of Self-Repair
There are two kinds of self repairing mechanics for units in BAR.

1.  **Continuous Repair** (`AutoHeal`): A set amount of HP that the unit constantly repairs every second.
2.  **Delayed Repair** (`Idle AutoHeal`): A set amount of HP that a unit repairs after not receiving damage for a set amount of time (`idleTime`). Idle time length is set by `idletime = 1800`, which at 1.00x game speed would be 1800/30 = 60 seconds
    
## Units with Unique autoHeal Values
| Category | Unit Name| autoHeal Value  |
|--|:-:|:-:|
|Building|Armada Fortification Wall|12|
|Building|Armada Dragon's Teeth| 4 |
| Building|Armada Shark's Teeth | 4 |
| Building|Cortex Fortification Wall | 12 |
| Building|Cortex Dragon's Teeth| 4 |
| Building|Cortex Shark's Teeth | 4 |
| Bot|Armada Gunslinger | 50 |
| Bot| Armada Webber |15 |
| Bot|Armada Commander | 5 |
| Bot|Armada Butler | 5 |
| Bot|Cortex Commando | 9 |
| Bot|Cortex Commander | 5 |
| Vehicle|Cortex Printer | 5 |
| Ship|Armada Convey | 5 |
| Ship|Armada Ellysaw | 1.5 |
| Ship| Armada Skater |1.5 |
| Ship|Cortex Brimstone | 1.5 |
| Ship|Cortex Coffin |5 |
| Ship|Cortex Herring| 1.5 |
| Ship|Cortex Riptide | 1.5 |
| Submarine|Armada Eel | 2 |
| Submarine|Armada Grim Reaper | 2 |
| Submarine|Cortex Orca| 2 |
| Submarine|Cortex Death Calvary | 2 |
     
## Auto Heal Calculation
Self-repairing is calculated through the following formula:

    if (health < maxHealth) { 
	    health += (unitDef->idleAutoHeal * (restTime > unitDef->idleTime)); 
	    health += unitDef->autoHeal; 
	    health = std::min(health, maxHealth); 
    } 

### Code Overview

The code checks if a unit's **current health** (`health`) is less than its **maximum health** (`maxHealth`). If true, the unit's health is healed incrementally using two different healing factors:

 - **Continuous Repair**: A smaller constant healing value that applies regardless of the idle state.
 - **Delayed Repair**: Conditional healing that applies only if the unit has been idle for a specified time.

Finally, the health is capped at the unit's maximum health.

	autoHeal     = udTable.GetFloat("autoHeal",      0.0f) * (UNIT_SLOWUPDATE_RATE * INV_GAME_SPEED);
	idleAutoHeal = udTable.GetFloat("idleAutoHeal", 10.0f) * (UNIT_SLOWUPDATE_RATE * INV_GAME_SPEED);
	idleTime     = udTable.GetInt("idleTime", 600);

### Note
The engine multiplies the autoheal by `15 * 1/30` as part of `autoHeal     = udTable.GetFloat("autoHeal",      0.0f) * (UNIT_SLOWUPDATE_RATE * INV_GAME_SPEED);`
