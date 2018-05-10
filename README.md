# mobile-metrics-example

This is an example of how the probe-scraper would access a github repository, and how the files in that repository might look.

## Histograms.json

Initial changes to the format below. Otherwise, this file follows the format set in [mozilla-centra Histograms.json](https://dxr.mozilla.org/mozilla-central/source/toolkit/components/telemetry/Histograms.json).

The file also includes all of the `telemetry_test` histograms.

### `release_channel_collection`

This field is new, and replaces `releaseChannelCollection`. Instead of `opt-out` and `opt-in`, it is `release` or `pre-release`. A `pre-release` probe is only recorded
on pre-release, e.g. nightlies or betas. A `release` probe is still recorded on pre-release channels, but also on the release channel.

### `github_issues`

This field is the github issue numbers associated with the probe. The issues should be in the same repository that the `Histograms.json` file is located in.

## Histograms.yaml

The yaml file for histograms is almost a direct mapping from the `Histograms.json`, with a few small modifications.

### `representation`

This field contains all of the fields necessary to make a representation of the histogram. As an example, we need the `low`, `high`, and `n_buckets` to create a representation
of a linear kind histogram; thus the representation might be:

```
representation:
  kind: linear
  low: 1
  high: 10
  n_buckets : 11
```

Which would give us a histogram with buckets `0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10`. The `0` buckets is the underflow buckets.

### Whitespace

Added whitespace after each probe definition makes the file more human-readable.

## Scalars.yaml

There is one additional field. Otherwise, this file follows the format set in [mozilla-central Scalars.yaml](https://dxr.mozilla.org/mozilla-central/rev/tip/toolkit/components/telemetry/Scalars.yaml).

### `github_issues`

This field is the github issue numbers associated with the probe. The issues should be in the same repository that the `Scalars.yaml` file is located in.
