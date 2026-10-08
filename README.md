# Volleyball Scoresheet v22

Live volleyball scoring that prints a hand-completed-looking NCAA scoresheet. It's a single file (`index.html`) with both scoresheet forms built in, no build step, and it works offline.

## Screens
- **Home:** Start new match, or Load previous match. Matches that aren't finalized are listed for quick access, and Previous matches has a search box, Open, Download and Delete for every match, plus Import a match file.
- **End of a match:** after the last set's review, the scoresheets open. Closing them shows the Finalize match box. Finalizing asks you to confirm (or go back), then saves the match as finalized, downloads a copy of the match file, and returns to the home screen. Finalized matches open read-only, with Reopen for corrections if something needs fixing.
- **Main screen:** score, sets won, timeouts, substitutions and challenges for each team. The court shows each position with the net at the top. A substituted player shows who they came in for ("for #14"), and the libero shows "L1 for #18".
- **Substitution:** one row per service position. Each row shows who is on the court and everyone who has played that position this set (earlier players struck through). It then lists the bench players who can come in for that player. Players who already played the position are marked *returns*. One tap records the sub, and the confirmation has an Undo link.
- **After each set:** confirming the score opens that set's finished scoresheet, with buttons to print it or the libero tracking sheet, then continues to the next set's lineups.
- **Match setup:** four tabs: Match, Teams & rosters, Officials, Rules. Rosters can be typed ("1 3 5 7 12") or picked from the full number list. If anything is missing, the form jumps to the tab that needs it.

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
  - Can't enter position I to serve if she already served from a different position that set; the main screen also warns before the serve.
  - Only replaces back-row players.
  - A completed rally between exit and re-entry (except entering at position I to serve).
  - Serves in only one rotation position per set.
  - Must leave before the serve if they rotate to the front row.
- Captains: the game captain is chosen from the starters. When the captain leaves the court, the app asks for a floor captain once and remembers that player for the rest of the match, so the next time it picks them automatically. The set's starting captain becomes captain again whenever they return to the floor. A libero can be floor captain.
- Timeouts per set, plus media timeouts.
- Sanctions: improper request, yellow card, red card. A red card gives the point and the serve to the opponent.
- Sets to 25 (deciding set to 15), win by 2. Prompts the side change after set 2 (2026 NCAA rule 9.2.4; no switch at 8 in set 5).
- Exceptional substitution (injury/illness): doesn't count toward the limit, and the player removed can't return that set.
- Technical timeout (sets 1–4) and media timeout, written in Comments.
- Challenge review (CRS, optional in Match Info): 2 per team per match. A reversed challenge is kept, and a fifth set adds one (max 2). After a reversal the app offers to correct the last rally.

## Scoresheet
The **Division** chosen in Match Setup picks the form automatically:

| Division | Form | Substitutions |
|---|---|---|
| NCAA Division I | 2026-27 NCAA Division I scoresheet | count boxes 1–15 (default limit 15) |
| NCAA Division II / III | 2026-27 NCAA Division II/III scoresheet | count boxes 1–18 (default limit 18) |
| NAIA Women's / Men's | NAIA scoresheet | unlimited, no count on the form |
| NJCAA, NCCAA, High School, Club, Other | NCAA Division II/III scoresheet | count boxes 1–18 |

All forms have a running score to 36. When the libero serves, a triangle is drawn over that rotation's Roman numeral in the Serving Order column, and the libero's serves are triangles on the service line and in the running score.

Substitutions are written the paper way: in the Players' Numbers box, the player leaving is slashed and the incoming number is written next to it, left to right, for every sub in that position. The service line also gets S in/out (Sx when the team is receiving), and the Substitutions count is slashed.

Scoresheet notation follows the 2026 NCAA scoring procedures. The captain is written "2c". A replay is a "P" in the service circle. Subs requested together are written as one entry ("Sx7/4, 3/6"). A player removed by exceptional substitution is circled instead of slashed. Challenges are written in Comments.

## Libero tracking sheet
The Scoresheet viewer has a **Libero tracking** tab, which prints portrait. It uses the NCAA D-I, NCAA D-II/III or NAIA form, matching the division. One sheet covers the whole match:
- S circled for the team serving first; team name; L1 and L2 (x when there's none).
- Service column: one tally each time that position starts a term of service.
- SP: starting player (c = captain).
- Substitution: the leaving number is slashed and the entering number written to its right (circled for an exceptional sub).
- Libero replacement: "L" after the replaced number, which isn't slashed. When that player returns, the number is written again after the L. Exchanges between liberos aren't recorded.
- A triangle around the Roman numeral where the libero served.
- Team substitution count slashed (D-I 15, D-II/III 18; none on NAIA).
- Challenge tables: set, score (challenging team first), and outcome circled.

One Letter-landscape page per set for the scoresheet. Use **Print this set** or **Print all sets**, then choose "Save as PDF" for a digital copy.

## Data
Every match is saved automatically in this browser's storage on this device and listed under Previous matches. Clearing the browser's site data removes them, so keep the match files downloaded at finalize (or use Download) as the permanent record.

- The match saves automatically on the device.
- **Backup → Export** writes a match file that **Import** can load on another device.
- Matches saved by v15–v21 are upgraded automatically, and the old data is kept as a backup.

Handwriting fonts: Kalam and Mrs Saint Delafield, SIL Open Font License.
