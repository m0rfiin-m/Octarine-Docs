# PC Building & Hardware

**Last Updated:** October 24, 2025

---

## Overview

Marco's PC hardware knowledge, cooling solutions, and component selection decisions.

---

## Current Build

### Core Components
- **CPU:** AMD Ryzen 9 7900X (170W TDP)
- **Motherboard:** Gigabyte B650M AORUS ELITE AX
- **RAM:** Issues with proper seating/placement
- **Case:** Montech Air 100
  - CPU cooler clearance: 161mm
  - Good airflow design
- **Storage:** Multiple drives across C:\, D:\, E:\

### Cooling System
- **Original:** Thermalright Frost Commander 240mm AIO
  - Performance: 55°C idle, 80°C gaming
  - **Problem:** Undersized for Ryzen 9 7900X's heat output
  - Considered returning

- **Upgrade Path:** Thermalright Peerless Assassin 120 SE
  - Height: 155mm (fits Montech Air 100's 161mm clearance)
  - **Versions:**
    - Standard SE ARGB White
    - Digital version (adds temperature display screen, $5-10 more)
  - **Expected Performance:**
    - 40-45°C idle (10-15°C improvement)
    - 68-75°C gaming (5-10°C improvement)
  - Dual tower with 6 heat pipes
  - Outperforms 240mm AIOs for sustained loads
  - No pump noise or failure risk
  - Price: $35-40

---

## Cooling Philosophy

### Air vs AIO
**Why Peerless Assassin Better:**
- More cooling capacity than 240mm radiators
- Doesn't heat-soak like small radiators
- More reliable (no pump to fail, no leaks)
- Better for sustained high loads
- Perfect for $35-40 price point

**240mm AIO Limitations:**
- Too small for high-TDP CPUs (170W+)
- Heat-soak during extended gaming
- Pump can fail
- More expensive

---

## Fan Configuration

### Proper Setup
**Pump (if using AIO):**
- Always 100% flat speed
- Never use "Auto" for pump
- Constant speed prevents cavitation

**Radiator/Tower Fans:**
- Use CPU temperature sensor (Tctl/Tdie)
- Create aggressive curve:
  - 30°C → 30% speed
  - 50°C → 45% speed
  - 70°C → 85% speed
  - 75°C → 100% speed
- Hysteresis: 3°C (prevents constant speed changes)
- Response time: 2 seconds

**Case Fans:**
- Can use their own curves
- Not as critical as CPU cooling

### Fan Control Software
- Fan Control (open source)
- MSI Afterburner
- SpeedFan
- BIOS/UEFI control

---

## Component Selection Lessons

### Cooler Sizing
- Match cooler to CPU TDP + headroom
- 240mm AIO minimum for 170W TDP
- High-end air coolers often outperform small AIOs
- Don't trust marketing - check independent reviews

### Case Compatibility
- Always verify cooler height clearance
- Montech Air 100: 161mm clearance
- Peerless Assassin 120 SE: 155mm (6mm clearance)

---

## Building Process Issues

### RAM Installation
- Experienced issues with RAM not properly seated
- Check motherboard manual for correct slot configuration
- Usually A2/B2 slots for dual-channel
- Fully insert until clicks heard

### AIO Installation
**Top Mount Setup:**
1. Radiator goes exterior (top of case)
2. Fans mount inside (below radiator)
3. Fans face down (smooth side toward motherboard)
4. Air pulls from case, exhausts through radiator

**Common Mistakes:**
- Radiator inside case (wrong)
- Fans facing wrong direction
- Everything crammed under top panel

---

## RGB Control

### OpenRGB
- **Purpose:** Unified RGB control across components
- **Setup:** Task Scheduler task at logon
- **Configuration:**
  - Profile: Specific color/pattern preset
  - Action: `"C:\Path\To\OpenRGB.exe" --profile "ProfileName"`
  - Run with highest privileges
  - Trigger: At log on

**Profile Loading:**
- Loads profile and exits immediately
- No window stays open
- RGB changes apply and persist

---

## Upgrade Considerations

### Cooling Upgrade Path
1. Verify current temps and identify bottleneck
2. Check case clearances before buying
3. Consider air over small AIOs for high-TDP CPUs
4. Budget option: Peerless Assassin 120 SE ($35-40)
5. Premium option: Noctua NH-D15 or similar

### Future Upgrades
- GPU not mentioned (likely satisfied with current)
- More RAM if needed
- Storage expansion to additional drives

---

## Troubleshooting Hardware

### Temperature Issues
**High Temps at Idle/Load:**
1. Check cooler mounting (proper contact)
2. Verify thermal paste application
3. Check fan curves (too aggressive or too passive)
4. Verify case airflow (intake/exhaust balance)
5. Clean dust filters

**Tools:**
- HWiNFO64 (temp monitoring)
- Fan Control (fan curve management)
- Ryzen Master (CPU monitoring)
- Task Manager (quick temp check)

---

**Related:** [[Windows System Management]], [[Technical Setup]]
