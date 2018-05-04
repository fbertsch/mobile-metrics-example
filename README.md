# mobile-metrics-example

This is an example of how the probe-scraper would access a github repository.

## Histograms.json

Initial changes to the format below. Otherwise, this file follows the format set in [mozilla-centra Histograms.json](https://dxr.mozilla.org/mozilla-central/source/toolkit/components/telemetry/Histograms.json).

### `release_channel_collection`

This field is new, and replaces `releaseChannelCollection`. Instead of `opt-out` and `opt-in`, it is `release` or `prerelease`. A `prerelease` probe is only recorded
on prerelease, e.g. nightlies or betas. A `release` probe is still recorded on prerelease channels, but also on the release channel.

### `releaseChannelCollection`

This field has been deprecated in favor of `release_channel_collection`

### `github_issues`

This field is the github issue numbers associated with the probe. The issues should be in the same repository that the `Histograms.json` file is located in.

## Scalars.yaml

There is one additional field. Otherwise, this file follows the format set in [mozilla-central Scalars.yaml](https://dxr.mozilla.org/mozilla-central/rev/tip/toolkit/components/telemetry/Scalars.yaml).

### `github_issues`

This field is the github issue numbers associated with the probe. The issues should be in the same repository that the `Scalars.yaml` file is located in.
