# shotwell-export
USAGE: shotwell-export firstfile lastfile destdir [db]

Export from shotwell between dates of firstfile and lastfile, inclusive, taking into account duplicate filenames. Also converts avi videos to mp4 and gzips original avi, and sets the MediaCreateDate on all exported videos (Shotwell does not do this) so they are ordered correctly in Google Photos and Amazon Drive (and maybe others?)

No meta data is set (except for MediaCreateDate on videos). You need to set this in Shotwell.

To get firstfile and lastfile, in Shotwell select file then View -> Extended Information, copy the Location field

If destdir does not exist in will be created

By default ~/.local/share/shotwell/data/photo.db is used, but this can be changed with the optional parameter db.

Requires sqlite3.
If ffmpeg cannot be found then avi file will not be transcoded to mp4.
If gzip does not exist avi files will not be gzipped after being transcoded.
If exiftool cannot be found videos will not have MediaCreateDate set.

Variables SQLITE, FFMPEG, GZIP, and EXIFTOOL can be set to point to a specific executable if you do not want to use the version in the PATH.

EXAMPLE:

shotwell-export "~/OldiPhotoLibrary/Masters/2009/Roll 104/PB230008.JPG" "~/OldiPhotoLibrary/Masters/2009/Roll 104/PB260046.JPG" ~/MyExport
