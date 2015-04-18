# tennis_pointbypoint
Sequential point-by-point data for tens of thousands of pro matches

Each row in these files represents one match, and contains the following:
- date
- tournament name
- tour (ATP, CH[allenger], FU[tures], WTA, or ITF [women])
- draw (Main [draw] or Qual[ifying])
- server1 (the player who served first)
- server2
- winner (1 or 2, corresponding to one of the previous two columns)
- pbp (see below)
- score
- adf_flag (1 if the point sequence notes any aces or double faults, 0 if not; see below)

The pbp field:

Each point is described with one character:
- S (server won)
- R (returner won)
- A (ace)
- D (double fault)

Sets are delimited with the '.' character, games are delimited with the ';' character, and the '/' character indicates changes of serve during a tiebreak.

Aces and double faults are not always noted in the original source data, which is why there is an adf_flag column. A '0' in that column indicates only that there are no aces or double faults recorded in the match, not whether aces or dfs *would've* been recorded had their been any. Matches without either are fairly rare, but they do happen.

The files themselves are separated by level, gender, and draw (same as the 'tour' and 'draw' columns in each sheet). The '_current' files contain 2015 matches, and the '_archive' files contain earlier matches, most of which are from 2012-14.

Compiling, parsing, and cleaning up this rather messy dataset has been an enormous task, and I've done what I can to present only relatively clean data. For instance, all match scores have been validated to eliminate obvious errors in the source data. One casualty in this approach is the exclusion of retirements, the scores of which are not 'valid'. However, there are surely many errors remaining, including mis-classified matches and mis-parsed matches which result in valid but incorrect scores. There are probably also some duplicate matches.

The combination of incomplete source data, my probably imperfect parser, and my when-in-doubt-exclude approach means that while this dataset is extremely extensive (74,000 matches as of April 2015), it is not complete for any sizable subset of matches. There is very good coverage for ATP and WTA tour-level main draw events since 2012 or 2013. The lower the level, the less complete.
