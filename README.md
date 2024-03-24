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
      winget install Python.Python.3.6
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

My intention with this is to have it work in a way that's useful for me especially with my media apps and, most importantly, for DJing.
It is indeed not following the typical format found everywhere but on Spotify for example.

This is that last part (DJing) that justified some decisions taken here such as :

* Getting rid of parentheses as much as possible (usually version / mix mentions), ie. Spotify's way
  | Before | After |
  | --- | --- |
  | Forever (Stay Like This) `(`Club Mix`)` | Forever (Stay Like This) `- `Club Mix |
  
  >It's really clearer for me when reading really quickly track names on the players' screens and it keeps the little lyrics mention available for checking and searching.
* Unify version calling (Radio edits become the « normal » version and original or whatever that's more suitable for mixing is called « extended »)
  | Before | After | Length |
  | --- | --- | --- |
  | Going Down` - Radio Edit` | Going Down | `3:03` |
  | Going Down | Going Down` - Extended` | `4:38` |

  >Indeed, this does not follow the artist's intent but I'm trying to keep some sanity when managing my library on Engine and Rekordbox and doing that allows me to then filter really fast for longer / mixable versions.
* Move « feat.(ured) » artists to the artists fields
  >This is not typical format but not necessarily false as those _featured_ artist still worked on the track in some way and are normally still getting royalties for those.
  >So, I move them to the end of the artists field, remove the « feat. » mention. That declutters the title for easy reading (again).
  >Search will still function without issue and it'll have the advantage of making the tracks of the « featured » artist show up on their artist page when I'm browsing for listening.
* When there's multiple people as an album's artist, only use the first one for creating the directory that will contain its albums
  | Before | After |
  | --- | --- |
  | * […] | * […] |
  | * Ofenbach  | * Ofenbach |
  | * Oliver Heldens | * Oliver Heldens |
  | * Oliver Heldens, Anabel Englund | * Oliver Tree |
  | * Oliver Heldens, Boy Matthews| * […] |
  | * Oliver Heldens, DJs From Mars, JD Davis |
  | * Oliver Heldens, Funkin Matt, Bright Sparks |
  | * Oliver Heldens, KAREN HARDING |
  | * Oliver Heldens, Kylie Minogue |
  | * Oliver Heldens, Mesto |
  | * Oliver Heldens, Nile Rodgers, House Gospel Choir |
  | * Oliver Heldens, Piero Pirupa |
  | * Oliver Heldens, Vula |
  | * Oliver Heldens, Shantel |
  | * […] |
  | * Oliver Tree |
  | * […] |

  >See how many directories do we have here already and I only wrote a fraction of OH's stuff. It becomes absolutely cluttered really fast just by following a single artist.
  >I usually put the most significant artist (for me) at the beginning anyway and simplifying that enables not having multiple directories containing only a single album for basically the same artist like shown.
  >Now, for probably the most crucial part, let's hypothesize that my prepped library does not get recognized on my drive plugged on the setup I need to perform or maybe I didn't account for said setup prior to stepping up.
  >I'll most likely have to navigate through files instead because the players' OS probably didn't check the files' data for tags (looking at you Rekordbox OS). In those cases, it (the enormous amount of folders) makes it really slow to go through my library when scrolling with the browsing knob with so many folders and even frustrating when looking for a song but don't know which other artists other than the main (OH in this case) were involved.
  >So, that cleans up things and saves me time and stress while performing on stage.
* Keeping track of labels and catalog numbers for releases
  >The catalog numbers especially are lifesavers for publishing tracklists with the right info or providing the promoters and broadcasters with the right music info for royalties.
  >I put them in the album's folder name just in case it gets lost in the tags or something.
* Have high quality cover arts residing as a file on the side (`cover.png`) _and_ have resized to lower resolution (max 1500px) version embedded in files
  >DJ players & softwares mostly only use embedded cover arts and some software & device OSes really dislike having huge cover art images.
  >On the other hand, the great cover art qualities are really useful for playing media on TVs when gathering. But those apps (say Emby) do use the cover art files stored alongside.
* Convert lossless files in FLAC if not already in that format
  >I have yet to encounter setups that don't support FLAC files. Sure, if speaking of DJing, CDJ-2000s don't support it for example.
  >But, when I had to use a venue's setup, they were setup with either DJ software on a computer or at least CDJ-2000NXS-es. (Those came out in 2016!)
  >Indeed, AIFF is TIFF (which I like) but for audio and, like TIFF, has some pretty cool features.
  >Although, I like that FLAC has lossless compression by default and has more flexibility with metadata.
  >It's handy for saving some storage space when you're broke and for leasure listening when streaming out and abroad.

## Useful extra tools 🛠️

* [COV - Cover Search Engine](https://covers.musichoarders.xyz/)
* [Ben Dodson's Apple Music Artwork Finder](https://bendodson.com/projects/apple-music-artwork-finder/)
* [Ben Dodson's iTunes Artwork Finder](https://bendodson.com/projects/itunes-artwork-finder/index.html)

## Contributing 🏗️

Contributions are absolutely welcome! I enjoy sharing my stuff and I love learning from others.
Just make sure to have at least a summary explaining the changes you are suggesting to merge so that I can understand what's going on.
Therefore, feel free to fork this repository and issue a pull request with your suggestion(s). 💛
