# CS2 Case Bot V1.4 - Detailed Setup Guide

**Created by Mk4gtiguy**

## Prerequisites

* [Streamer.bot](https://streamer.bot) v1.0.4 or higher installed
* Your streaming platform connected (Twitch, YouTube, or Trovo)

\---

## Step 1: Add Persisted Globals (Skin Lists)

1. Open Streamer.bot
2. Go to **Services** → **Global Variables** → **Persisted Globals**
3. Open `persisted-globals.txt` from this repo
4. Copy each line (one at a time) and click **Add New Variable**
5. Paste the name and value
6. Repeat for all 55+ skin lists

\---

## Step 2: Create Core Actions

For each command, follow these steps:

### Create the Action

1. Right-click in Actions panel → **Add Action**
2. Name it (e.g., `CS2\_OpenCase`)

### Add C# Code

1. Click **Add Sub-Action** → **Core** → **C# Code**
2. Paste the code from `V1.4-Complete-Code-Reference.md`
3. Click **Compile** (should show no errors)

### Set Trigger (for commands)

1. Click **Triggers** tab
2. Click **Add Trigger** → **Command**
3. Enter the command name (e.g., `!case`)

### Special: Case\_Command Sub-Action

For the `!case` command only:

1. After the C# code, click **Add Sub-Action**
2. Select **Core** → **Actions** → **Run Action**
3. Select `CS2\_OpenCase` as the target

\---

## Step 3: Required Actions List

### Core Actions

|Action Name|Trigger|Special Notes|
|-|-|-|
|CS2\_OpenCase|(none)|Sub-Action only|
|Case\_Command|`!case`|Must run CS2\_OpenCase|

### Case Management

|Action Name|Trigger|
|-|-|
|SetCase\_Command|`!setcase`|
|CaseInfo\_Command|`!caseinfo`|
|CaseStats\_Command|`!casestats`|

### Economy and Inventory

|Action Name|Trigger|
|-|-|
|Inv\_Command|`!inv`|
|Sell\_Command|`!sell`|
|SellAll\_Command|`!sellall`|
|SellAllConfirm\_Command|`!sellallconfirm`|
|SellHelp\_Command|`!sellhelp`|
|Balance\_Command|`!balance`|
|Daily\_Command|`!daily`|
|Tradeup\_Command|`!tradeup`|
|InventoryValue\_Command|`!inventoryvalue`|

### Streaks and Badges

|Action Name|Trigger|
|-|-|
|Streak\_Command|`!streak`|
|Badges\_Command|`!badges`|

### Trading and Gifting

|Action Name|Trigger|
|-|-|
|Trade\_Command|`!trade`|
|AcceptTrade\_Command|`!accepttrade`|
|DenyTrade\_Command|`!denytrade`|
|Gift\_Command|`!gift`|

### Jackpot

|Action Name|Trigger|Permission|
|-|-|-|
|Jackpot\_Command|`!jackpot`|Everyone|
|JackpotInfo\_Command|`!jackpotinfo`|Everyone|
|Jackpot\_Draw|`!jackpotdraw`|Mods Only|

### Stats and Leaderboards

|Action Name|Trigger|
|-|-|
|MyStats\_Command|`!mystats`|
|Odds\_Command|`!odds`|
|TopMoney\_Command|`!topmoney`|
|TopInventory\_Command|`!topinventory`|
|TopGolds\_Command|`!topgolds`|
|TopOpens\_Command|`!topopens`|

### Admin Commands (Moderator+)

|Action Name|Trigger|Permission|
|-|-|-|
|GiveBalance\_Command|`!givebalance`|Moderator|
|TakeBalance\_Command|`!takebalance`|Moderator|
|GiveItem\_Command|`!giveitem`|Moderator|
|ResetUser\_Command|`!resetuser`|Moderator|
|SetCasePrice\_Command|`!setcaseprice`|Moderator|

### Help

|Action Name|Trigger|
|-|-|
|Help\_Command|`!help`|

\---

## Step 4: Set Permissions

1. Find each action with restricted permissions
2. Click **Triggers** tab
3. Click the trigger → Set **Permission**:

   * `!jackpotdraw` → **Moderator**
   * All admin commands → **Moderator** (or Broadcaster)

\---

## Step 5: Test Your Bot

In your chat, type these commands one at a time:

```text
!help
!setcase Dreams
!balance
!daily
!case
!inv
!sell
!streak
!badges



If everything works, you're ready to go!



\---



\## Troubleshooting



\### "CPH does not contain a definition for 'GetArg'"

\- Use `args\["rawInput"].ToString()` instead



\### Case won't switch

\- Use `!setcase Dreams` not `!case Dreams`



\### Jackpot not working

\- Ensure `!jackpotdraw` is mods only

\- Check that `JackpotPot` and `JackpotEntries` globals exist



\### Balance always $0

\- Run `!daily` first to get starting money



\### Trade not working

\- Use item numbers from `!inv` (e.g., `!trade @user 3`)



\### Selling issues

\- Type `!sell` alone to see numbered inventory

\- Then `!sell 2` to sell item #2



\---



\## Need Help?



\- Open an issue on GitHub

\- Join the Streamer.bot Discord



\---



\## Support



If this bot helps your stream, consider supporting me on Ko-fi:



https://ko-fi.com/mk4gtiguy

