# NIMRODS Mods

A clean, optimized collection of mods for the game NIMRODS using MelonLoader.

## 🎮 Available Mods

### SpawnMod
Spawns additional enemies and mini-bosses to increase game difficulty and action.

**Features:**
- Configurable extra enemy spawns (0-10+ recommended)
- Smart entity cap system to prevent performance issues
- Excludes problematic enemy types (splitters, special spawns)
- **Automatic mini-boss spawning** with 8 different mini-bosses:
  - **Forest:** Bertha, Carl, Charrrger, GangGang Leader, Splitserpent, Vipress
  - **Barrens:** Betty, Charlie, Dingleberry
- **Boss Difficulty Selection:**
  - **Normal:** Standard difficulty bosses only
  - **Mixed:** Random mix of normal and hard mode bosses
  - **Hard:** Challenging hard mode bosses only
- **Extra Boss Spawning:** Configure how many bosses spawn per interval (1-3 total)
- **Time-based progression** - different mini-bosses available at different stages
- Real-time debug logging

### UnlimitedRerollsMod
Provides unlimited rerolls for Gambler Pods.

**Features:**
- Unlimited rerolls for Gambler Pod weapon upgrades
- No token consumption
- Debug logging for troubleshooting
- Seamless integration with game UI

### CollectionRangeMod
Dramatically increases pickup range for XP orbs and collectibles.

**Features:**
- Massive collection range boost
- Affects XP orbs, items, and power-ups
- Safe implementation with coroutine-based timing
- Debug logging for range modifications

### EnemyScalingMod
Comprehensive enemy stat scaling system for increased challenge and XP rewards.

**Features:**
- **Health Scaling**: Increase enemy health (1.0 = normal, 2.0 = double health)
- **Damage Scaling**: Boost enemy damage output (1.0 = normal, 2.0 = double damage)
- **Movement Speed Scaling**: Make enemies faster (1.0 = normal, 1.5 = 50% faster)
- **Armor Scaling**: Increase enemy armor/defense (1.0 = normal, 2.0 = double armor)
- **Projectile Fire Rate Scaling**: Make enemies shoot faster (1.0 = normal, 2.0 = double fire rate)
- **Ability Cooldown Scaling**: Make enemy abilities recharge faster (1.0 = normal, 1.5 = 50% faster)
- **Time-Based Scaling**: Enemies get stronger as you survive longer (10% per minute)
- **XP Scaling System**: Enemies drop more XP based on their toughness
  - **Stat-Based XP**: Health and speed contribute to XP bonus (max 50% total)
  - **Time-Based XP**: Longer survival = more XP (max 100% after 24 minutes)
  - **Additive Bonuses**: All XP bonuses stack additively for predictable scaling
  - **Maximum XP**: 2.5x total XP (150% bonus) with maximum settings
- **Smart Integration**: Uses the game's native stat system for full compatibility
- **Performance Optimized**: Efficient stat application without memory leaks

## 🚀 Installation

### Prerequisites
- NIMRODS game (Steam)
- MelonLoader Nightly build version 0.7.2-ci.2291 installed in your NIMRODS directory

### Setup Steps
1. **Download** the mod DLL files from the release
2. **Copy** all `.dll` files to your NIMRODS `Mods` folder:
   ```
   C:\Program Files (x86)\Steam\steamapps\common\NIMRODS\Mods\
   ```
3. **Copy** `ModConfig.jsonc` to your NIMRODS game directory:
   ```
   C:\Program Files (x86)\Steam\steamapps\common\NIMRODS\
   ```
   ⚠️ **Important:** You must copy this file to get the helpful comments and explanations!
4. **Launch** the game and enjoy enhanced gameplay!

### Required Files
Copy these files to the specified locations:

**To `NIMRODS/Mods/` folder:**
- `SpawnMod.dll`
- `UnlimitedRerollsMod.dll` 
- `CollectionRangeMod.dll`
- `EnemyScalingMod.dll`
- `SharedModConfig.dll`

**To `NIMRODS/` root directory:**
- `ModConfig.jsonc`

## ⚙️ Configuration

The `ModConfig.jsonc` file contains detailed comments explaining each setting:

```json
{
  // NIMRODS Mods Configuration
  // Save this file to apply changes instantly (no restart needed)
  
  "SpawnMod": {
    // Extra enemies per original spawn (0=off, 1=double, 2=triple, etc.)
    "ExtraSpawns": 1,
    
    // Enable/disable this mod
    "Enabled": true,
    
    // Skip special formation spawns (circle/square/clump) - recommended: true
    "ExcludeSpecialSpawns": true,
    
    // Skip splitter enemies that multiply when killed - recommended: true
    "ExcludeSplitters": true,
    
    // Max enemies on screen before stopping spawns (lower = better performance)
    "MaxEnemyEntities": 2500,
    
    // Show debug messages in game console
    "ShowDebugMessages": false,
    
    // Enable automatic mini-boss spawning during gameplay
    "EnableMiniBossSpawning": true,
    
    // Time interval between mini-boss spawns (in seconds)
    "MiniBossSpawnInterval": 30.0,
    
    // Boss difficulty selection (0=Normal, 1=Mixed, 2=Hard)
    "BossDifficulty": 0,
    
    // Extra bosses to spawn (0=1 boss, 1=2 bosses, 2=3 bosses total)
    "ExtraBossSpawns": 0
  },
  
  "RerollMod": {
    // Unlimited weapon upgrade rerolls for Gambler Pods
    "Enabled": true,
    "ShowDebugMessages": false
  },
  
  "CollectionRangeMod": {
    // Massive pickup range for XP orbs and items
    "Enabled": true,
    "ShowDebugMessages": false
  },
  
  "EnemyScaling": {
    // Enable/disable enemy scaling
    "Enabled": true,
    
    // Health multiplier for enemies (1.0 = normal, 2.0 = double health)
    // Also affects XP scaling: higher health = more XP (max 30% bonus at 5x health)
    "HealthMultiplier": 1.0,
    
    // Damage multiplier for enemies (1.0 = normal, 2.0 = double damage)
    "DamageMultiplier": 1.0,
    
    // Movement speed multiplier for enemies (1.0 = normal, 1.5 = 50% faster)
    // Also affects XP scaling: higher speed = more XP (max 20% bonus at 4x speed)
    "MovementSpeedMultiplier": 1.0,
    
    // Armor multiplier for enemies (1.0 = normal, 2.0 = double armor)
    // Note: Enemies without armor get 1 base armor before scaling
    "ArmorMultiplier": 1.0,
    
    // Whether XP should scale based on enemy stats (health and movement speed)
    // Uses actual stat values (including time scaling) for XP calculations
    // Max 50% total bonus: 30% from health, 20% from speed
    "ScaleXPWithStats": true,
    
    // Whether stats should scale with survive time
    // Time scaling: 10% increase per minute (0.1 factor)
    // After 24 minutes: 3.4x multiplier on all stats
    "ScaleWithTime": true,
    
    // Time scaling factor (0.1 = 10% increase per minute of survive time)
    // Higher values = faster stat progression, lower values = slower progression
    "TimeScalingFactor": 0.1,
    
    // Show debug messages when scaling is applied
    // Useful for understanding how XP scaling works
    "ShowDebugMessages": false
  }
}
```

## 🔥 Hot-Reload Feature

**Real-time configuration changes without restarting the game!**

1. Edit `ModConfig.jsonc` while playing
2. Save the file
3. Changes apply automatically within seconds
4. Check game logs for confirmation

Perfect for fine-tuning difficulty and performance on the fly.

## 🎯 Performance Tips

- **Start with `ExtraSpawns: 1`** and increase gradually
- **Keep `ExcludeSplitters: true`** to prevent exponential lag
- **Lower `MaxEnemyEntities`** if experiencing framerate drops
- **Adjust `MiniBossSpawnInterval`** for challenge level (10s = hard, 30s = moderate, 60s = easy)
- **Enable debug messages** only when troubleshooting
- **Boss Difficulty:** Start with Normal (0), try Mixed (1) for variety, Hard (2) for challenge
- **Enemy Scaling:** Start with multipliers at 1.0, increase gradually for challenge
- **Time Scaling:** 0.1 = 10% increase per minute, 0.05 = 5% increase per minute

## 🎮 XP Scaling Configuration

The EnemyScalingMod includes an advanced XP scaling system that rewards players for taking on tougher enemies and surviving longer.

### **How XP Scaling Works:**

**Stat-Based XP (Max 50% bonus):**
- **Health contribution**: Up to 30% bonus based on actual enemy health
- **Speed contribution**: Up to 20% bonus based on actual enemy speed
- **Uses real values**: Accounts for time scaling and other modifiers

**Time-Based XP (Max 100% bonus):**
- **Progressive scaling**: XP increases as you survive longer
- **24-minute cap**: Reaches maximum 100% bonus after 24 minutes
- **Linear progression**: ~4.17% increase per minute

**Additive System:**
- **Simple math**: All bonuses are added together
- **Maximum possible**: 50% (stats) + 100% (time) = 150% total bonus = 2.5x XP

### **Configuration Examples:**

#### **Conservative XP Scaling**
```json
"HealthMultiplier": 1.5,      // +3.75% XP from health
"MovementSpeedMultiplier": 1.2, // +1.3% XP from speed
"ScaleXPWithStats": true,
"ScaleWithTime": true
```
**Result**: ~5% stat bonus + time scaling = 1.05x to 2.05x XP

#### **Moderate XP Scaling**
```json
"HealthMultiplier": 3.0,      // +15% XP from health
"MovementSpeedMultiplier": 2.0, // +6.7% XP from speed
"ScaleXPWithStats": true,
"ScaleWithTime": true
```
**Result**: ~22% stat bonus + time scaling = 1.22x to 2.22x XP

#### **Maximum XP Scaling**
```json
"HealthMultiplier": 1.5,      // Reaches 5.1x health after 24 minutes
"MovementSpeedMultiplier": 1.2, // Reaches 4.08x speed after 24 minutes
"ScaleXPWithStats": true,
"ScaleWithTime": true
```
**Result**: 50% stat bonus + 100% time bonus = 2.5x XP maximum

#### **Precise 5x Health, 4x Speed Scaling**
```json
"HealthMultiplier": 1.47,     // Reaches exactly 5.0x health after 24 minutes (1.47 × 3.4)
"MovementSpeedMultiplier": 1.18, // Reaches exactly 4.0x speed after 24 minutes (1.18 × 3.4)
"ScaleXPWithStats": true,
"ScaleWithTime": true
```
**Result**: 50% stat bonus + 100% time bonus = 2.5x XP maximum

### **Time Scaling Impact:**

With `TimeScalingFactor: 0.1` (default):
- **5 minutes**: 1.5x stat multiplier
- **10 minutes**: 2.0x stat multiplier
- **15 minutes**: 2.5x stat multiplier
- **24 minutes**: 3.4x stat multiplier (maximum)

**⚠️ Important:** The TimeScalingFactor should be a small value (0.05-0.2). Values like 2.0 will cause extreme scaling:
- **0.5 minutes**: 2.0x scaling (too fast!)
- **1 minute**: 3.0x scaling
- **5 minutes**: 11.0x scaling (broken!)

**Recommended values:**
- **0.05**: Slow progression (5% per minute)
- **0.1**: Normal progression (10% per minute) - **Default**
- **0.15**: Fast progression (15% per minute)
- **0.2**: Very fast progression (20% per minute)

### **Debug Information:**

Enable `"ShowDebugMessages": true` to see:
- `"XP Stat Scaling: Health=450.0 (4.5x, +26.3%), Speed=9.0 (3.0x, +13.3%), Total Stat Bonus=+39.6%"`
- `"XP Time Scaling: 12.5 minutes (+52.1%)"`
- `"XP Multiplier: 1.00 -> 1.92 (total bonus: +91.7%, multiplier: 1.92)"`

## 🎯 Advanced Scaling Features

The EnemyScalingMod now includes advanced scaling for enemy combat behavior, making mini-bosses and bosses more challenging and dynamic.

### **Projectile Fire Rate Scaling:**

**What it affects:**
- **Gang Gang**: Rapid projectile barrages
- **Dingleberry**: Projectile pattern attacks
- **Splitserpent**: Heavy projectile volleys
- **Bertha**: Slow but powerful projectiles
- **Charlie**: Fast projectile attacks

**How it works:**
- **`ProjectileFireRateMultiplier: 1.0`** = Normal fire rate
- **`ProjectileFireRateMultiplier: 2.0`** = Enemies shoot twice as fast
- **`ProjectileFireRateMultiplier: 0.5`** = Enemies shoot half as fast
- **Time scaling**: Fire rate increases with survival time

**Configuration examples:**
```json
// Moderate challenge
"ProjectileFireRateMultiplier": 1.5,  // 50% faster shooting

// High challenge
"ProjectileFireRateMultiplier": 2.0,  // Double fire rate

// Reduced challenge
"ProjectileFireRateMultiplier": 0.7,  // 30% slower shooting
```

### **Ability Cooldown Scaling:**

**What it affects:**
- **Bee Boss**: Charge/dash attacks
- **Mini-bosses**: Special moves and abilities (character abilities only)
- **Any enemy**: Abilities that have cooldowns

**Note:** Only affects character abilities (index 0). Underbarrel abilities are primarily used by player weapons, not enemies.

**How it works:**
- **`AbilityCooldownMultiplier: 1.0`** = Normal recharge speed
- **`AbilityCooldownMultiplier: 1.5`** = Abilities recharge 50% faster (more aggressive enemies)
- **`AbilityCooldownMultiplier: 2.0`** = Abilities recharge twice as fast (very aggressive enemies)
- **Time scaling**: Recharge speed increases with survival time (enemies become more aggressive)

**Configuration examples:**
```json
// More aggressive abilities
"AbilityCooldownMultiplier": 1.5,  // Abilities recharge 50% faster

// Normal behavior
"AbilityCooldownMultiplier": 1.0,  // Standard cooldown speed

// Very aggressive abilities
"AbilityCooldownMultiplier": 2.0,  // Abilities recharge twice as fast
```

### **Advanced Configuration Examples:**

#### **Aggressive Mini-Bosses**
```json
"ProjectileFireRateMultiplier": 2.0,  // Shoot twice as fast
"AbilityCooldownMultiplier": 1.5,     // Abilities recharge 50% faster
"ScaleWithTime": true
```
**Result**: Mini-bosses become much more aggressive over time

#### **Balanced Challenge**
```json
"ProjectileFireRateMultiplier": 1.3,  // 30% faster shooting
"AbilityCooldownMultiplier": 1.2,     // 20% faster ability recharge
"ScaleWithTime": true
```
**Result**: Moderate increase in difficulty that scales with time

#### **Defensive Enemies**
```json
"ProjectileFireRateMultiplier": 0.7,  // 30% slower shooting
"AbilityCooldownMultiplier": 0.8,     // 20% slower ability recharge
"ScaleWithTime": true
```
**Result**: Enemies become less aggressive, easier to manage

### **Debug Information:**

Enable `"ShowDebugMessages": true` to see:
- `"Projectile Fire Rate: 1.20 -> 2.40 (multiplier: 2.00)"`
- `"Ability Cooldown: 0.80 -> 1.20 (multiplier: 1.50)"`
- `"Final Stats - Health: 150.0, Speed: 4.5, Melee: 45.0, Projectile: 30.0, Armor: 3.0, Fire Rate: 2.40, Ability CD: 1.20"`

## 🐛 Troubleshooting

**Mods not loading?**
- Verify MelonLoader Nightly build version 0.7.2-ci.2291 is installed
- Check that all `.dll` files are in the `Mods/` folder
- Ensure `ModConfig.jsonc` is in the game root directory
- Check MelonLoader console for error messages

**Performance issues?**
- Reduce `ExtraSpawns` value (try 1 or 2)
- Lower `MaxEnemyEntities` cap (try 1500 or 2000)
- Keep `ExcludeSplitters: true`
- Disable other performance-heavy mods temporarily

**Configuration not working?**
- Verify `ModConfig.jsonc` syntax using a JSON validator
- Check file location and permissions
- Enable debug messages to see what's happening
- Look for "Configuration loaded" messages in logs

**Game crashes?**
- Start with all mods disabled (`"Enabled": false`)
- Enable one mod at a time to identify the problem
- Check MelonLoader logs for error details
- Ensure you're using MelonLoader Nightly build version 0.7.2-ci.2291

## 📋 What You Get

After installation, your game will have:

### Enhanced Gameplay
- **2x to 10x more enemies** (configurable)
- **Automatic mini-boss spawning** with 8 different mini-bosses for increased challenge
  - **Boss Difficulty Selection:** Choose between Normal, Mixed, or Hard mode bosses
  - **Extra Boss Spawning:** Spawn 1-3 bosses per interval
  - **Time-based progression** - different mini-bosses available at different stages:
    - **0-4:15:** Splitserpent, Dingleberry only
    - **4:15-8:15:** + Bertha added to pool
    - **8:15-12:15:** + Carl Jr, Charlie added to pool  
    - **12:15+:** All mini-bosses available (except final boss)
  - Random selection from appropriate pool for current game time
- **Unlimited Gambler Pod rerolls** for better builds
- **Massive pickup range** for smoother gameplay

### Smart Performance Management
- **Automatic entity limits** prevent lag
- **Problematic enemy exclusions** avoid crashes
- **Dynamic performance scaling** based on game state

### User-Friendly Configuration
- **Commented config file** explains every setting
- **Hot-reload support** for instant changes
- **Debug logging** for troubleshooting

## 📝 Version Information

- **SpawnMod:** v1.1.0 - Enhanced boss spawning with difficulty selection
- **UnlimitedRerollsMod:** v1.1.0 - Unlimited weapon upgrade rerolls
- **CollectionRangeMod:** v1.1.0 - Enhanced pickup range
- **EnemyScalingMod:** v1.1.0 - Comprehensive enemy stat scaling
- **SharedModConfig:** v1.1.0 - Centralized configuration system

## 📝 License

Educational use only. Use at your own risk.

---

**Enjoy the enhanced NIMRODS experience! 🚀**