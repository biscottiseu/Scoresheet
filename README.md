# Digital Volleyball Scoresheet v9

Changes in v9:
- Server verification is now embedded directly in the scoring buttons.
- Immediately after lineups are confirmed, the serving team's point button becomes `SERVE BY #` and the receiving team's point button is disabled.
- All pre-serve actions remain available before the serve is verified, including libero exchanges, substitutions and timeouts.
- Tapping the active `SERVE BY #` button at service contact records server verification and unlocks both point buttons.
- After every point, the app returns to the same pre-serve verification state for the next rally.
- Removed the old server verification popup and secondary confirmation step.
- Uses a new v9 local-storage key to avoid incompatible saved state from prior builds.
