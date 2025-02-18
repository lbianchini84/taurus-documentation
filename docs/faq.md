# FAQ

It's not you; it's us.
Taurus is not a simple representation, and
we frequently get questions about how to use it to represent certain kinds of data.
This page attempts to answer some of those questions.

## Where do I store statistics about my measurements

Let's say that you have data for the same kind of measurement being repeated multiple times.
For example, you take a sample from your material, subdivide it 8 times, and perform the
same measurement on each of those 8 sub-samples.
The measurement that you are performing can be represented by a single
[`MeasurementSpec`](../specification/objects/#measurement-spec)
and each of those 8 sub-samples as its own
[`MeasurementRun`](../specification/objects/#measurement-run)
associated with that spec.
Each
[`MeasurementRun`](../specification/objects/#measurement-run)
is associated with the
[`MatererialRun`](../specification/objects/#measurement-run)
representing the material that you sampled and sub-divided.

For each property in the
[`MeasurementRun`](../specification/objects/#measurement-run)
objects, you may want to compute some statistics of the 8-sample distribution.
For example: the mean and the standard deviation of each property and/or its minimum and maximum values.
In the future, these statistics will be automatically computed on the Citrine platform.
For now, you can compute them yourself and record them in another
[`MeasurementRun`](../specification/objects/#measurement-run)
object distinct from the 8 samples.
If there are multiple properties and/or multiple statistics, they should all go in the same `MeasurementRun`.
The statistics should be
[`Property`](../specification/attributes/#property)
attributes with their `origin` field set to `computed`.
