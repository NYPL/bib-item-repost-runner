# Bib/Item Reposter Runner

This is a small module for executing bulk post requests against the Bib/Item services.

## Initialization

```
cp config/sample.env config/[environment].env
```

Fill your environment file with meaningful config.

## Running

```
node index TYPE [NYPLSOURCE] [STARTINGID] [--limit LIMIT] [--batchSize BATCHSIZE] [--batchDelay BATCHDELAY]
```

 * `TYPE`: Either "bibs" or "items".
 * `NYPLSOURCE`: Specify the nyplSource (Must be one of: 'sierra-nypl', 'recap-pul', 'recap-cul')
 * `STARTINGID`: Optional starting id, e.g. 'b13410675'. Default '0', i.e. the lowest id in the store.
 * `LIMIT`: Optional integer limit, e.g. 1000. Default 1000.
 * `BATCHSIZE`: Optional integer batch size, e.g. 100. Default 100.
 * `BATCHDELAY`: Optional integer delay in ms to wait between batches, e.g. 100. Default 0.

For example, this will cause the Bibs service to re-post the first 1000 `sierra-nypl` bibs into the `Bibs` stream:

```
node index bibs sierra-nypl
```

And this will post 50K `recap-pul` items starting at id 'id1234567' in batches of 100:

```
node index items recap-pul id1234556 --limit 50000 --batchSize 100
```