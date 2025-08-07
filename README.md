# NIMRODS Mod Suite

A collection of gameplay enhancement mods for NIMRODS that add configurable difficulty scaling, quality-of-life improvements, and extended gameplay mechanics.

## 🚀 Installation

### Requirements
- **Game:** NIMRODS (Steam)
- **Framework:** MelonLoader Nightly build v0.7.2-ci.2291+ 
- **Platform:** Windows 10/11 (64-bit)

### Setup
1. **Install MelonLoader** to your NIMRODS directory 
   - https://github.com/LavaGang/MelonLoader/releases
2. **Copy mod files** to `NIMRODS/Mods/`:
   - `SpawnMod.dll`
   - `UnlimitedRerollsMod.dll` 
   - `CollectionRangeMod.dll`
   - `EnemyScalingMod.dll`
   - `SharedModConfig.dll`
3. **Copy config file** to `NIMRODS/` root:
   - `ModConfig.jsonc`
4. **Launch the game** - mods will load automatically

## 🎮 Available Mods

### 🔥 SpawnMod - Enemy Spawning & Mini-Boss System
Increases enemy density and adds automatic mini-boss spawning with configurable difficulty.

**Key Features:**
- **Extra Enemy Spawns:** Scale from 1x to 10x+ enemy density
- **Mini-Boss System:** 8 different mini-bosses spawn automatically every 30 seconds
- **Boss Difficulty:** Choose Normal, Mixed, or Hard mode bosses
- **Multi-Boss Spawning:** Spawn 1-3 bosses per interval
- **Time Progression:** Different bosses unlock as you survive longer
- **Smart Performance:** Automatic entity caps prevent lag
- **Safe Filtering:** Excludes problematic enemies (splitters, special formations)

**Mini-Boss Timeline:**
- **0-4:15 min:** Splitserpent, Dingleberry
- **4:15-8:15 min:** + Bertha
- **8:15-12:15 min:** + Carl Jr, Charlie  
- **12:15+ min:** All mini-bosses available

### 🎰 UnlimitedRerollsMod - Gambler Pod Enhancement
Removes reroll token costs from Gambler Pods for unlimited weapon upgrade experimentation.

**What it does:**
- **Unlimited Rerolls:** No more token costs for weapon upgrade rerolls
- **Build Testing:** Experiment with different weapon combinations freely
- **Seamless Integration:** Works with existing Gambler Pod UI

### 🧲 CollectionRangeMod - Enhanced Pickup Range
Dramatically increases pickup range for XP orbs and items for smoother gameplay.

**What it does:**
- **Massive Range Boost:** Pick up items from much further away
- **All Collectibles:** Affects XP orbs, items, and power-ups
- **Smooth Gameplay:** Reduces tedious movement for pickups

### ⚔️ EnemyScalingMod - Enemy Stat Scaling
Scales enemy stats to create customizable difficulty that increases over time.

**Scaling Options:**
- **Health:** 1.0x (normal) to 10x+ (tank enemies)
- **Damage:** 1.0x (normal) to 5x+ (devastating attacks)
- **Movement Speed:** 1.0x (normal) to 4x+ (lightning fast)
- **Armor:** 1.0x (normal) to 10x+ (heavily armored)

**Time-Based Scaling:**
- **Progressive Difficulty:** Enemies get stronger as you survive longer
- **Default:** 10% stat increase per minute (configurable)
- **Formula:** Stats = Base × Multiplier × (1 + surviveTime/60 × 0.1)
- **Example:** After 10 minutes, 2x health becomes 4x health

## ⚙️ Configuration

Edit `ModConfig.jsonc` to configure all mods. Changes apply instantly without restarting the game.

### Key Settings

**SpawnMod:**
- `ExtraSpawns`: 0-10+ (0=off, 1=double enemies, 2=triple, etc.)
- `MiniBossSpawnInterval`: 15-60 seconds between boss spawns
- `BossDifficulty`: 0=Normal, 1=Mixed, 2=Hard
- `ExtraBossSpawns`: 0-2 (spawn 1-3 bosses per interval)

**EnemyScaling:**
- `HealthMultiplier`: 1.0-10.0+ (enemy health scaling)
- `DamageMultiplier`: 1.0-5.0+ (enemy damage scaling)
- `MovementSpeedMultiplier`: 1.0-4.0+ (enemy speed scaling)
- `ScaleWithTime`: true/false (enemies get stronger over time)
- `TimeScalingFactor`: 0.05-0.2 (how fast scaling increases per minute)

## 🎯 Performance Tips

**Recommended Starting Settings:**
- `ExtraSpawns`: 1 (double enemies)
- `HealthMultiplier`: 1.5 (50% more health)
- `TimeScalingFactor`: 0.1 (10% increase per minute)
- Keep `ExcludeSplitters: true` to prevent lag

**For Better Performance:**
- Lower `MaxEnemyEntities` if experiencing lag
- Increase `MiniBossSpawnInterval` for easier gameplay
- Start with lower multipliers and increase gradually

## 🐛 Troubleshooting

**Mods not loading?**
- Verify MelonLoader v0.7.2-ci.2291+ is installed
- Check all `.dll` files are in `NIMRODS/Mods/` folder
- Ensure `ModConfig.jsonc` is in NIMRODS root directory

**Performance issues?**
- Lower `ExtraSpawns` (try 1-2)
- Reduce `MaxEnemyEntities` (try 1500-2000)
- Keep `ExcludeSplitters: true`

**Configuration not working?**
- Check `ModConfig.jsonc` syntax with a JSON validator
- Enable debug messages to see what's happening
- Look for "Configuration loaded" in MelonLoader console

## 📝 Version Information

- **SpawnMod:** v1.1.0 - Boss spawning with difficulty selection
- **UnlimitedRerollsMod:** v1.1.0 - Unlimited weapon rerolls
- **CollectionRangeMod:** v1.1.0 - Enhanced pickup range
- **EnemyScalingMod:** v1.1.0 - Enemy stat scaling
- **SharedModConfig:** v1.1.0 - Configuration system

## 📝 License

Educational use only. Use at your own risk.