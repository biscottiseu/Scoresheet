# Volleyball Scoresheet v20

This build replaces the custom scoresheet report with a digital-ink overlay on the actual NCAA non-deciding-set scoresheet layout supplied for the project. Match setup, lineups, service results, running score, substitutions, timeouts, officials, set timing and final result are positioned on the paper form. New scoring events also store structured service/substitution/timeout metadata so the sheet can reproduce NCAA notation more accurately.

The renderer follows the supplied NCAA instructions: service contacts/results are recorded on service-order lines, non-libero serves use circles, libero serves use triangles, receiving-team rally wins are rotate marks/slashes, substitutions are tied to the appropriate service-order line and substitution count, and timeouts are recorded in the timeout boxes.
