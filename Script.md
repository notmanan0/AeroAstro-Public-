# Lecture transcription script

Transcribes every lecture recording in `~/Downloads/Panopto` with [OpenAI Whisper](https://github.com/openai/whisper) and saves a `.txt` transcript next to each video. Run it in PowerShell.

- Picks up `.mp4`, `.mkv`, `.mov`, `.m4v`, `.webm` and `.avi` files.
- Each video is transcribed into its own temporary folder, so Whisper's other outputs (`.srt`, `.vtt`, `.tsv`, `.json`) are discarded.
- Never overwrites: if `<name>.txt` already exists, the transcript is saved as `<name> (transcript).txt`.
- Requires `whisper` on the PATH (`pip install -U openai-whisper`) and `ffmpeg`.

```powershell
$dir = "$HOME\Downloads\Panopto"; $vids = Get-ChildItem -LiteralPath $dir -File | Where-Object { $_.Extension -in '.mp4','.mkv','.mov','.m4v','.webm','.avi' }; foreach ($v in $vids) { $tmp = Join-Path $env:TEMP ("whisper_" + [guid]::NewGuid()); New-Item -ItemType Directory -Path $tmp | Out-Null; whisper "$($v.FullName)" --output_dir "$tmp" --language en; $src = Join-Path $tmp "$($v.BaseName).txt"; if (Test-Path -LiteralPath $src) { $dest = Join-Path $dir "$($v.BaseName).txt"; if (Test-Path -LiteralPath $dest) { $dest = Join-Path $dir "$($v.BaseName) (transcript).txt" }; Move-Item -LiteralPath $src -Destination $dest; Write-Host "Saved: $dest" -ForegroundColor Green } else { Write-Host "No transcript for $($v.Name)" -ForegroundColor Red }; Remove-Item -LiteralPath $tmp -Recurse -Force }
```

Once the transcripts are made, drop them (with the slides) into the relevant `Year N/` folder and run `/weekly` to file them and write the notes.
