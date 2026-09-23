# Digital Volleyball Scoresheet v4

Fixes a storage/undo bug that could freeze scoring after a few rallies. Event undo snapshots now store only match state rather than recursively embedding the full event history. Uses a new local-storage key so the broken v3 state does not carry into this version.
