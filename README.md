# Volleyball Scoresheet Prototype v10

Changes from v9:
- Pre-serve alternate actions (libero exchange, substitution, timeout, note) are enabled only while waiting for server verification.
- Once the serve is verified, those actions lock and only point entry is available until the rally is scored.
- A libero on the court is marked with an L beside the jersey number in the court grid.
- The regular player replaced by the libero moves to a visible REPLACED box below the court.
- Clicking the replaced-player box returns that regular player through the tracked libero replacement sequence.
- Saved state uses a new v10 key to avoid older prototype state conflicts.
