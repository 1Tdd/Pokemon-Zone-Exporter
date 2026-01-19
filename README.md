# Pokemon Zone Exporter
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

I made this script for you if you don't want to have to type in card counts by hand anymore. By automating the data export, it connects [pokemon-zone.com](https://www.pokemon-zone.com) with the tracker at [tcgpocketcollectiontracker.com](https://tcgpocketcollectiontracker.com).


The Main Idea
One amazing thing about Pokemon Zone is that it can get your card data from your Nintendo account. But that's where the information stays. 

This script enables you take that collection that syncs automatically and put it in a CSV file that the external tracker can read. It takes care of all the mapping of the expansion and set codes and fixes the problems with overcounting (like when foil variations screw with your unique card count).

## What the Script Does - **Accurate Deduplication**: It uses `InternalId` to find your true unique cards. This avoids the extra space that expansion variants (foils, etc.) add.
- **Click-Saving Automation**: Automatically clears the search bar, resets your advanced search filters, and forces "Collection #"/Ascending order before it scans.
- **Watching SPA: You don't need to refresh. The script only waits for you to go to the `/cards/` page because the site is a Single Page App.
- **Auto-Scrolling**: It automatically clicks the "Load More" buttons for you until all the cards are loaded.

## How to utilize it 
1. Install [Tampermonkey](https://www.tampermonkey.net/). 
2. **Install the userscript**:
   
   [![Download](https://img.shields.io/badge/Download-Latest_Release-blue?style=for-the-badge&logo=github)](https://github.com/1Tdd/Pokemon-Zone-Exporter/releases/latest/download/PokemonZoneExporter.user.js) 
3. Open your cards page on Pokemon Zone. 
4. Hit **Scan Collection**.  Just wait for it to finish and say "Ready!". 
5. Click **Save CSV File** and upload it to the [import page](https://tcgpocketcollectiontracker.com). 

## Technical Junk 
The script employs a massive hardcoded map of `InternalId`s to bridge both platforms.  If the export crashes after a new set release, that map normally just requires an update with the new card IDs. 

### ⚠️ A Note on Risks & ToS >  [!CAUTION] 
> **Read this before you sync your account.** > >  Nintendo is particularly tight about data.  Their ToS simply prevents "unauthorized third-party software" from touching their servers.  Since Pokemon Zone's "Sync" feature logs into your account to get data, it technically falls under this. > > **The logout thing**:  When you sync on Pokemon Zone, it causes a logout on your mobile app ("session collision").  This is because the server is pretending to be your device to acquire the data. 
> > - **Use at your own risk**:  The true sync on Pokemon Zone is the part that touches official services.  This script only reads the output HTML, but the whole operation is technically "off-grid." 
> - **No Warranty**:  I'm just a programmer that wrote this to make my life simpler.  I have no ties to Pokemon Zone or Nintendo, and I'm not responsible for anything that occurs to your account. 

--- *By 1Tdd*