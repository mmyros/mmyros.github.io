# Things I wish I knew before starting a relational database
## Why relational
- Checks on data inegrity means you can pass your project to the maintainers
- Lower barrier to try out ideas on old data 

## Staying sane
- Separate phases of analysis: ingestion/condensing, chunking, computation, organization, plotting
- Write two schemas at a time, one you're thinking about now and its child
- First, populate a few recording sessions, not all datasets
- Once the current schema and its child seem to work fine, get them populating and move on the the next node. Work on whole analysis simultaneously - no need to wait for all step to finish. Can start next as soon as a few keys have populated. 
- My data entry stage is during recording when I make the filename 
- Keep Datetime as primary key for restrictions on populate calls (Not so sure anymore)
- baby steps at the top, cram many at the bottom - bottom is high overhead due to multiplication of keys (eg events), whereas dropping top nodes means recalculate all children
For populate calls, restrict by list of fids if you suspect that some are not populating due to errors
- Xarray populate must not be parallelized or dropped - dj doesn't check it
- if not all items are showing up at the end of populate, repeat with reserve=False
- start with reserve=False for schemas that require little cpu
- If you work on children and parents simultaneously,  parents may not show up for a while. wait until mysql processes them first.

## Gotchas
- fractional primary keys must be stored as decimal  (10,30)
