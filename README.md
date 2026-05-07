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
$images=@('.jpg','.jpeg','.png','.bmp','.gif','.ico','.tif','.tiff','.webp','.jfif','.heic')

foreach($image in $images){
    cmd /c assoc $image=AppX43hn07pmpsxe668av6vsk5744vy0m6v2
}

foreach($image in $images){
    cmd /c assoc $image
}
