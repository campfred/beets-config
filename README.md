# Beets config

My very opiniated configuration for the Beets music library utility.

## Setup 📥

Here's how to get setup my Beets configuration.

1. Clone this repository
   >You can clone it in [the default location](https://docs.beets.io/en/latest/reference/config.html#id133) if you prefer.
   >Just don't forget to set up your backups to include it.
2. Configure a `BEETSDIR` environment variable to point to this repository
3. Configure the `Editor` environment variable to point to preferred text editor as I'm using the [Edit plugin which depends on that](https://beets.readthedocs.io/en/latest/plugins/edit.html)
   >In my case, for VSCode obtained from WinGet, it is : `code.cmd --wait` .
4. Prepare your system with required packages
   1. Windows

      ```powershell
      winget import --import-file winget-packages.json
      ```

      or

      ```powershell
      winget install Microsoft.VisualStudio.2022.BuildTools --force --override "--wait --passive --add Microsoft.VisualStudio.Component.VC.Tools.x86.x64 --add Microsoft.VisualStudio.Component.Windows11SDK.22000" # https://stackoverflow.com/a/55053709
      winget install Rustlang.Rustup
      winget install ImageMagick.ImageMagick
      winget install Gyan.FFmpeg
      winget install gstreamerproject.gstreamer
      winget install AcoustID.Chromaprint
      winget install Python.Python.3.12
      ```

      then

      ```powershell
      # Refresh environment variables
      $env:Path = [System.Environment]::GetEnvironmentVariable("Path","Machine") + ";" + [System.Environment]::GetEnvironmentVariable("Path","User")
      ```

   2. Python

      ```shell
      python -m pip install --upgrade pip
      pip install --requirement requirements.txt
      ```

***Voilà!***
Now, you can use Beets as always. 🎉

## But why is it setup that way? 🤔

My intention with this is to have it work in a way that's useful for me especially with my media apps (gonic + Airsonic (refix)) and, most importantly, for DJing.
It is indeed not following the typical format found everywhere but on Spotify for example.

_This is that last part (DJing) that pushed me to make some decisions taken here._

###### Getting rid of parentheses as much as possible (usually versions / mix mentions), ie. Spotify's way

Basically replacing them with a simple hyphen.

| Before                                  | After                                 |
| --------------------------------------- | ------------------------------------- |
| Forever (Stay Like This) `(`Club Mix`)` | Forever (Stay Like This) `- `Club Mix |

>It's really clearer for me when reading track names really quickly on the players' screens and it keeps the little lyrics mention available for checking and searching.

###### Unify version names

_Radio edits_ or shorter versions become the « normal » versions and _Original_ or whatever that's suitable for mixing is called « extended » unless it's the only existing version.

| Before                    | After                   | Length |
| ------------------------- | ----------------------- | ------ |
| Going Down` - Radio Edit` | Going Down              | `3:03` |
| Going Down                | Going Down` - Extended` | `4:38` |

>Indeed, this does not follow the artist's intent but I'm trying to keep some sanity when managing my library on Engine and Rekordbox and doing that allows me to then filter really fast for longer / mixable versions.

###### Move « feat.(ured) » artists to the artists fields

This is not typical format but not necessarily false as those _featured_ artist still worked on the track in some way and are normally still getting royalties for those.
So, I move them to the end of the artists field, remove the « feat. » mention. That declutters the title for easy reading (again).
>Search will still function without issue and it'll have the advantage of making the tracks of the « featured » artist show up on their artist page when I'm browsing for listening.

###### Simplify artist folder structure

When there's multiple people as an album's artist, only use the first one for creating the directory that will contain its albums

| Before                                             | After            |
| -------------------------------------------------- | ---------------- |
| * […]                                              | * […]            |
| * Ofenbach                                         | * Ofenbach       |
| * Oliver Heldens                                   | * Oliver Heldens |
| * Oliver Heldens, Anabel Englund                   | * Oliver Tree    |
| * Oliver Heldens, Boy Matthews                     | * […]            |
| * Oliver Heldens, DJs From Mars, JD Davis          |                  |
| * Oliver Heldens, Funkin Matt, Bright Sparks       |                  |
| * Oliver Heldens, KAREN HARDING                    |                  |
| * Oliver Heldens, Kylie Minogue                    |                  |
| * Oliver Heldens, Mesto                            |                  |
| * Oliver Heldens, Nile Rodgers, House Gospel Choir |                  |
| * Oliver Heldens, Piero Pirupa                     |                  |
| * Oliver Heldens, Vula                             |                  |
| * Oliver Heldens, Shantel                          |                  |
| * […]                                              |                  |
| * Oliver Tree                                      |                  |
| * […]                                              |                  |

See how many directories do we have here already and I only wrote a fraction of OH's stuff. It becomes absolutely cluttered really fast just by following a single artist.
I usually put the most significant artist (for me) at the beginning anyway and simplifying that enables not having multiple directories containing only a single album for basically the same artist like shown.

Now, for probably the most crucial part, let's hypothesize that my prepped library does not get recognized on my drive plugged on the setup I need to perform or maybe I didn't account for the venue's setup prior to stepping in :

* I'll most likely have to navigate through files instead because the players' OS probably didn't check the files' data for tags (looking at you, Rekordbox OS and the way you handle user settings).
* In those cases, it (the enormous amount of folders) makes it really slow to go through my library when scrolling with the browsing knob with so many folders and even frustrating when looking for a song but don't know which other artists other than the main (OH in this case) were involved.

So, that cleans up things and saves me time and stress while performing on stage.

###### Keeping track of labels and catalog numbers for releases
The catalog numbers especially are lifesavers for publishing tracklists with the right info or providing the promoters and broadcasters with the right music info for royalties.

So, I put them in the album's folder name just in case it gets lost in the tags or something.

###### Cover art strategy

Have high quality cover arts residing as a file on the side (`cover.png`) _and_ have resized to lower resolution (max 1280px) version embedded in files.

That way, autonomous devices, especially DJ players, that may only use embedded cover arts won't freeze when loading tracks due to the processing time required for cover arts.
On the other hand, I still keep the great cover art qualities that are really useful for playing media on TVs during social gatherings.

###### Convert lossless files to FLAC

I have yet to encounter setups that don't support FLAC files.
Sure, if speaking of DJing, CDJ-2000s don't support it for example.
But, when I had to use a venue's setup, they were setup with either DJ software on a computer or at least CDJ-2000NXS-es. (Those came out in 2016!)

>Sure. AIFF is basically akin to TIFF (that I like) but for audio and, like TIFF, has some pretty cool features.
>Although, I like that FLAC uses (lossless) compression _by default_ and has _more flexibility with metadata_.
>It's really handy for saving some storage space when you're broke and for leasure listening when streaming out and abroad. 😅

## Useful extra tools 🛠️

* [COV - Cover Search Engine](https://covers.musichoarders.xyz/)
* [Ben Dodson's Apple Music Artwork Finder](https://bendodson.com/projects/apple-music-artwork-finder/)
* [Ben Dodson's iTunes Artwork Finder](https://bendodson.com/projects/itunes-artwork-finder/index.html)
* [Tunebat Song Key & BPM Finder](https://tunebat.com/Analyzer)

## Contributing 🏗️

Of course you can contribute!
Check the [CONTRIBUTING.md](CONTRIBUTING.md) file about it. 💛
