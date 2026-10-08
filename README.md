# Volleyball Scoresheet v22

Live volleyball scoring that prints a hand-completed-looking NCAA scoresheet. It's a static site with two files (`index.html` and `scoresheet-bg.png`), no build step, and it works offline.

## How it works
A match is stored as a **log of actions**: lineup, serve, rally, sub, libero, timeout, sanction, captain, note and set confirmation. Every action goes through one rules engine. The live screen, the match log and the printed sheet are all rebuilt from that log. Because of this:
- **Undo** is exact.
- **Edit** can safely correct an old entry. The whole match is re-checked, and if a later entry would stop being legal, the correction is refused with the reason.
- The scoresheet always matches what was scored.

## Rules enforced
- Lineups: six different starters from the roster, captain chosen from the starters, liberos not in the starting six.
- Server verification before every rally. Rotation only happens on a side-out (not on the first side-out of a set).
- Substitutions:
  - Limit per set.
  - A player who has played in one position can only return to that position.
  - The libero can't be subbed, and the player the libero replaced can't be subbed in.
- Libero:
  - Only replaces back-row players.
  - A completed rally between exit and re-entry (except entering at position I to serve).
  - Serves in only one rotation position per set.
  - Must leave before the serve if they rotate to the front row.
- Floor captain is requested when the game captain leaves the court.
- Timeouts per set, plus media timeouts.
- Sanctions: improper request, yellow card, red card. A red card gives the point and the serve to the opponent.
- Sets to 25 (deciding set to 15), win by 2. Prompts to switch sides at 8 in the deciding set.

## Scoresheet
One Letter-landscape page per set. Use **Print this set** or **Print all sets**, then choose "Save as PDF" for a digital copy.

## Data
- The match saves automatically on the device.
- **Backup → Export** writes a match file that **Import** can load on another device.
- Matches saved by v15–v21 are upgraded automatically, and the old data is kept as a backup.

Handwriting fonts: Kalam and Mrs Saint Delafield, SIL Open Font License.
