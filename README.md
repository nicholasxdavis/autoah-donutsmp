# AutoAH - Fabric Mod for Minecraft 1.21

Automated auction house mod for DonutSMP.

## Features

- Automatically opens `/ah chest` command
- Buys 64 wood chests (price range: 30k-60k) - buys individual chests until 64 total
- Places chests in double chest one at a time (one chest per slot)
- Fills hotbar with single chests (one per slot)
- Automatically runs `/ah sell 5000`
- Shows confirmation popup with clickable green glass pane

## Usage

1. Stand in front of a double chest (the chest you want to fill)
2. Run `/autoah toggle on` to start the automation
3. The mod will:
   - Open the auction house chest GUI
   - Search for and buy chests priced between 30,000-60,000 coins
   - Continue buying until you have 64 chests total
   - Place each chest in the double chest (one per slot)
   - Fill your hotbar with chests (one per slot)
   - Run `/ah sell 5000`
   - Show a confirmation screen with a green glass pane
4. Click the green glass pane to confirm the sale
5. Run `/autoah toggle off` to disable the automation

## How It Works

The mod uses a state machine to automate the entire process:
- **IDLE**: Waits for you to stand in front of a double chest
- **OPENING_AH_CHEST**: Executes `/ah chest` command
- **SEARCHING_CHEST**: Scans AH GUI for chests with valid prices (30k-60k)
- **BUYING_CHEST**: Clicks buy/confirm buttons to purchase chests
- **PLACING_IN_DOUBLE_CHEST**: Places chests one at a time in the double chest
- **FILLING_HOTBAR**: Fills hotbar slots with single chests
- **SELLING**: Executes `/ah sell 5000` command
- **WAITING_CONFIRMATION**: Shows confirmation screen

## Price Detection

The mod parses prices from item lore/tooltips. It looks for:
- Numbers followed by "coins", "k", "K", or "$"
- Prices in the range 30,000 - 60,000

## Building

```bash
# Windows
gradlew build

# Linux/Mac
./gradlew build
```

The built mod will be in `build/libs/autoah-1.0.0.jar`

## Installation

1. Install Fabric Loader for Minecraft 1.21
2. Install Fabric API (version 0.110.0+1.21 or compatible)
3. Place the mod JAR in your `.minecraft/mods/` folder
4. Launch Minecraft

## Requirements

- Minecraft 1.21
- Fabric Loader 0.16.9+
- Fabric API 0.110.0+1.21
- Java 21+

## Notes

- The mod is designed for DonutSMP's auction house plugin
- You may need to adjust slot indices if your AH plugin uses a different GUI layout
- The mod will show status messages in chat during automation
- Make sure you have enough coins to buy 64 chests (30k-60k each)

## Troubleshooting

- **Mod not starting**: Make sure you're standing directly in front of a double chest
- **Not buying chests**: Check that chests are available in the AH with prices 30k-60k
- **Slot errors**: The AH plugin GUI might use different slot layouts - adjust in `AutoAHAutomation.java`



