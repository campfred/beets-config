# About this repository

This repository is a music collection managed by the Beets.io Python program.
Its contents are miticulously curated and organized to ensure a high-quality in tag informations and to make it easier to use in a DJ-ing context.
The Python virtual environment must be activated to ensure that the correct dependencies are used when working with this collection.
Beets uses YAML files to define the tags of the songs being imported or edited in the collection.

## Tags handling

### Naming conventions

A few tag naming conventions are using commas to separate multiple values in a single tag.
This is done to ensure that music software that supports multiple values in a single tag can properly parse them.
Otherwise, it is useful to keep the tags consistent and easy to read.

#### Title naming convention

The song titles in this collection follow a specific format to ensure consistency and clarity. The format is as follows:

```
{title} - {version}
```

Here, the title is the name of the song, and the version indicates any specific remix, edit, or variation of that song.
In the case of an extended version, the word "Mix" is excluded to keep the title concise. For example, `Extended Mix` would simply be represented as `Extended`.
This format helps in distinguishing between different versions of the same track, which is particularly useful for DJs and music enthusiasts.

This naming convention is also applied to album titles when it comes to Singles and EPs for example.

In the case of a DJ mix, the title will be formatted as follows:

```
[{{event_name} {event_location} {event_year}|{event_hashtag}}] {stage?} {week?} {day?} {timing?} Set - {media_type}
```

For example:

```
[Tomorrowland Belgium 2023] Mainstage Week 1 Friday 8PM Set - Dry
```

Where:

-   `event_name` is the name of the event (e.g., "Tomorrowland")
-   `event_location` is the location of the event (e.g., "Belgium")
-   `event_year` is the year of the event (e.g., "2023")
-   `event_hashtag` is the hashtag associated with the event (e.g., "#Tomorrowland2023") if exists instead of the `event_name`, `event_location` and `event_year`
-   `stage` is the stage where the DJ played (e.g., "Mainstage")
-   `week` is the week of the event (e.g., "Week 1")
-   `day` is the day of the event (e.g., "Friday")
-   `timing` is the timing of the set (e.g., "8PM")
-   `media_type` is the type of media (e.g., "Dry" when no commentary is present)

Of course, the brackets and their contents are omitted if not applicable and the brackets themselves are also omitted.

#### Track artists naming convention

Since it happens often that a track is a collaboration between multiple artists, the artist names are simply separated by a comma and no `and` or `&` is used except when it is in the music act's name.
Artists that would appear as "featuring" in the title are instead included in the artists field of the track but as the last artist.

#### Album artists naming convention

The album artist field is following the same convention as the track artists, where multiple artists are separated by a comma, but the the "featured" artists are left out unless it is present on all of the tracks of the album.

#### Genre naming convention

The genre field of tracks is handled similarly to the artists field, where multiple genres are separated by a comma.

#### Label naming convention

The label names must not include the word `Records`, `Recordings` or `Music` at the end of the name to keep it more concise.

### Other tags

In all cases, comments need to be empty.

In extended mixes, the lyrics field need to be empty as these are not used on DJ decks. But the normal versions of the tracks must have the lyrics field kept as is as they come from trusted sources and are already accurate.

When it comes to the year tag, it must be a 4-digit number representing the year of release of the track or album.

Of course, the track total tag for each disc must be consistent with the number of tracks in a given disc (two discs can have a different number of tracks in them) and the disc total tag must also be consistent with the number of discs in the album.

### ID handling

The ID field is used by Beets to identify which YAML segment corresponds to which file in the database.
It is important to keep this ID intact when editing the YAML files to ensure that Beets can properly manage the music collection.
In the case of a mistmatched ID, Beets will discard the changes made to the YAML section.
When adding new music files to the collection, Beets will automatically assign a new ID to the new entries.

## Tracks organization within a multi-disc album

It will happen often that a Single or an EP will have multiple discs.
This is used to separate different versions of the same track, such as extended mixes.

For excample, a single might have the following tracks:

```
Disc 1:
1. Title 1
2. Title 2
Disc 2:
1. Title 1 - Extended
2. Title 2 - Extended
```

or

```
Disc 1:
1. Title - Someone Remix
Disc 2:
1. Title - Someone Extended
```

## Kind of assistance you may be requested for

You may be requested to assist in completing missing metadata during the import of new music files into the collection.
For example, you will be told that there is a specific disc that has the tags vetted but they need to be replicated to the other disc(s) of the album.
You will need to find the tracks that have been vetted and copy their tags to the other tracks of the album that are missing them.
However, you will need to ensure that the versions are correct. Meaning that if you're asked to replicate from the disc 2 to the disc 1, it's likely that the tracks you'll be completing the tags on will be the non-extended versions of the tracks.
This means that if the title of the track on disc 2 is `Title - Extended`, the title on disc 1 should be `Title` without the `- Extended` part.
Of course, the disc numbers are just examples and the actual disc numbers may vary. It could happen that an album has 3 discs for example where the first disc has the normal versions, the second disc has the extended versions and the third disc has instrumentals.
It can also happen that a multi-disc album (say one with 2 discs) but there are also two more discs that are the extended versions of the first two discs (so 4 discs in total).

## General suggestions

When assisting in completing missing metadata, indicate whenever there are potential mistakes in the tags.
There shouldn't be any trailing whitespace in the tags.
