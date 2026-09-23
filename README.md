# Volleyball Scoresheet v19

Fixes the paper scoresheet renderer crash caused by the renderer reading `s.score.A` instead of the app's actual `s.scores.A` state. Also aligns completed-set score/timing lookup with `setRecords`, fixes libero lookup from saved lineup data, and tags centrally logged future events with their set number for more reliable set-by-set rendering.
