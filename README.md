Restore Windows Image File Associations

This PowerShell script restores common image file extensions to the default Microsoft Photos application on Windows.

It uses the SFTA module to reassign image file associations and refreshes Windows Explorer so the changes apply immediately.

Supported File Extensions

The following image formats are restored:

.jpg
.jpeg
.jpe
.png
.bmp
.gif
.webp
.jfif
.tif
.tiff
Requirements

Before running the script:

Download or place SFTA.ps1 in:
C:\Temp\SFTA.ps1
Run PowerShell as Administrator.
Replace:
{{ progid }}

with the desired application ProgID.

What the Script Does

The script:

Loads the SFTA module
Verifies the module is available
Applies the selected ProgID to all supported image extensions
Restarts Windows Explorer
Immediately refreshes file associations
Notes
Some Windows policies or third-party applications may override file associations.
A system restart may occasionally be required.
Errors for individual extensions are ignored so the script can continue processing the remaining formats.