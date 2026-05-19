# Restore Windows Image File Associations

This PowerShell script restores common image file extensions to the default Microsoft Photos application association on Windows.

## Supported Extensions

The script updates associations for:

- .jpg
- .jpeg
- .png
- .bmp
- .gif
- .ico
- .tif
- .tiff
- .webp
- .jfif
- .heic

## PowerShell Script

```powershell
$ErrorActionPreference = "Stop"

          # FORCE load SFTA
          . "C:\Temp\SFTA.ps1"

          if (-not (Get-Command Set-FTA -ErrorAction SilentlyContinue)) {
              throw "SFTA not loaded"
          }

          $progid = "{{ progid }}"

          $exts = @(
            ".jpg",".jpeg",".jpe",".png",
            ".bmp",".gif",".webp",
            ".jfif",".tif",".tiff"
          )

          # STEP 1: APPLY ALL ASSOCIATIONS FIRST
          foreach ($e in $exts) {

              Write-Host "Setting $e -> $progid"

              try {
                  Set-FTA -ProgId $progid -Extension $e -Verbose
              }
              catch {
                  # Write-Host "FAILED $e $_"
              }
          }

          # STEP 2: force shell refresh AFTER all changes
          Start-Sleep -Seconds 2
          Stop-Process -Name explorer -Force -ErrorAction SilentlyContinue
          Start-Sleep -Seconds 2

          Write-Host "DONE"

