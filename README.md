# BadBuddha Enhanced OrderLine (Lite)

A NinjaTrader 8 indicator that displays position entry, profit targets, and stop losses with P&L calculations and risk/reward zone shading.

![NinjaTrader 8](https://img.shields.io/badge/NinjaTrader-8-blue)
![License](https://img.shields.io/badge/license-Free-green)
![Version](https://img.shields.io/badge/version-2.0.1.0-green)

---

## Overview

Enhanced OrderLine provides clear visual representation of your active trading positions directly on the chart. See your entry price, profit targets, and stop losses at a glance with dollar and tick calculations for each order.

**Key Features:**
- Position entry line display
- Profit target lines with cumulative P&L
- Stop loss lines with full position risk
- Risk/reward zone shading
- Configurable colors and label positioning

---

## Screenshots

<img width="1388" height="888" alt="image" src="https://github.com/user-attachments/assets/e7f0ce28-ad62-488e-ba60-bce184695c82" />

</p>


<img width="1392" height="902" alt="image" src="https://github.com/user-attachments/assets/335ec149-cccb-4cb8-abb1-05985ba2f340" />

---

## Features

| Feature | Description |
|---------|-------------|
| **Position Entry Line** | Shows your average entry price |
| **Profit Target Lines** | Dashed lines at each PT with $ profit and tick count |
| **Stop Loss Lines** | Dashed lines at each SL with $ risk and tick count |
| **Cumulative P&L** | PT labels show individual + cumulative profit |
| **Zone Shading** | Semi-transparent shading between entry and PT/SL |
| **Label Alignment** | Left, Center, or Right positioning |
| **Multi-Order Support** | Handles multiple PTs and SLs per position |
| **Auto-Update** | Checks for updates once per day |

---

## Installation

### Method 1: Import (Recommended)
1. Download the `.zip` file
2. In NinjaTrader 8, go to **Tools > Import > NinjaScript Add-On**
3. Select the downloaded file
4. Restart NinjaTrader

---

## Usage

1. Open a chart in NinjaTrader 8
2. Right-click > **Indicators**
3. Find **BadBuddha Enhanced OrderLine (Lite)** in the list
4. Click **Add** > **OK**

Lines appear automatically when you have an open position with working PT/SL orders.

---

## Configuration

### Display Settings

| Property | Default | Description |
|----------|---------|-------------|
| Line Thickness | 2 | Thickness of all lines (1-5) |

### Line Colors (Group 03)

| Property | Default | Description |
|----------|---------|-------------|
| Position Color | DodgerBlue | Entry line color |
| Profit Target Color | Lime | PT line color |
| Stop Loss Color | Red | SL line color |

### Shading (Group 04)

| Property | Default | Description |
|----------|---------|-------------|
| PT Shade Color | Lime | Profit zone shading color |
| PT Shade Opacity | 8 | Profit zone opacity (0-100%) |
| SL Shade Color | Red | Risk zone shading color |
| SL Shade Opacity | 8 | Risk zone opacity (0-100%) |

### Labels (Group 05)

| Property | Default | Description |
|----------|---------|-------------|
| Text Alignment | Right | Label position (Left/Center/Right) |
| Label Horizontal Offset | 100 | Pixels from chart edge |

### Update Settings (Group 02)

| Property | Default | Description |
|----------|---------|-------------|
| Enable Update Checks | True | Check for new versions |
| Update Cadence (Days) | 1 | Days between update checks |

---

## Understanding the Display

```
                                          +$150 / $150 (15t) x2
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - PT1
          [Profit Zone Shading]
_________________________________________________________ Entry @ 5250.00
          [Risk Zone Shading]
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - SL
                                          -$200 (20t) x2
```

### Label Format

**Profit Targets:**
```
+$150 / $300 (15t) x2
  ^      ^    ^    ^
  |      |    |    +-- Order quantity
  |      |    +------- Ticks from entry
  |      +------------ Cumulative profit (all PTs to this point)
  +------------------- This PT's profit
```

**Stop Losses:**
```
-$200 (20t) x2
  ^    ^    ^
  |    |    +-- Full position quantity
  |    +------- Ticks from entry
  +------------ Full position risk at this SL
```

---

## How It Works

### Order Detection
- **Profit Targets**: Identified by `IsLimit` property
- **Stop Losses**: Identified by `IsStopMarket` property
- Orders must be in `Working` or `Accepted` state

### P&L Calculation
```
Ticks = |Order Price - Entry Price| / Tick Size
Dollars = Ticks x Tick Value x Quantity
```

### Position Tracking
- Monitors the account selected in Chart Trader
- Automatically updates when orders are filled or modified
- Clears display when position is closed

---

## Troubleshooting

### Lines not showing
1. Ensure you have an open position on the chart's instrument
2. Verify PT/SL orders are in Working state (not pending)
3. Check that Chart Trader is connected to an account

### Labels misaligned
- Adjust **Label Horizontal Offset** in settings
- Try different **Text Alignment** options

### Performance issues
- The indicator uses optimized SharpDX rendering
- Reduce number of other indicators if issues persist

### Update popup not showing
- Ensure **Enable Update Checks** is True
- Check NinjaTrader Output Window for errors

---

## Support

- **Website**: [badbuddhacustoms.com](https://www.badbuddhacustoms.com)
- **Email**: support@badbuddhacustoms.com

---

## License

This indicator is **FREE** software by BadBuddha Customs LLC.

No license required for the Lite version.

---

## Author

**BadBuddha Customs LLC**

Building tools for traders who take their craft seriously.

---

*Know your risk before you enter.*
