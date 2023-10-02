# Audio and Video related

## increase volume with ffmpeg

`ffmpeg -i input.mkv -filter:a "volume=4.0" output.mkv`

## Convert all .avi files to .mkv

`for i in *.avi; do ffmpeg -i "$i" "${i%.*}.mkv"; done`
