# TraxAir API test spec

Status of the spec <img src="http://online.swagger.io/validator?url=https://raw.githubusercontent.com/Trax-air/traxair-api-test/master/swagger.json">

This API allows you to identify some tracks or some mixes.

# Paths

## /me
This path defines operations related to the user, which are at the moment billing information and callback urls.

The callback urls are linked to:
* __callbackTrackIdentification__: the track identification is finished
* __callbackTracklistIdentification__: a new track has been found in a mix
* __callbackTrackTerritoryChange__: the territory changed for a track.

## /track
Query all the `Track` objects from the TraxAir database, or add some new ones.

## /identify
### /identify/tracklist
Identify a mix from a file or from an url. This creates a `TracklistIdentification` resource  which contains metadata about the mix (provided by the user) and several runs of the identification which are contained in a `TracklistIdentificationRun object`. Reruns are triggered by a POST of a `RunParams` object on /identify/tracklist/{identificationId}. `RunParams` contains segments of audio that should be identified again (for example: rerun the identification between 0:01 and 0:15 because this part was unknown).

### /identify/track
Identify a track from a file or an url. The resources mirror the ones from _tracklist_. The `TrackIdentification` resource contains a `Track` resource.
