# MiiDataFiles
storing every single Mii data file that is available for download on the Mii Library. https://sites.google.com/view/miilibrary/home

# Types

## Wii Formats

* RCD
   * This format is very common for Wii-format Mii data files. It contains no checksum, and stores all information. It also has many unofficial filename extensions, such as .mii, .mae, or .miigx. RCD files are stored on the Mii Library with the .miigx, as fanmade tools have been made to directly import RCD files onto a Wii console, but only if the file extension is .miigx, so this aims to be more convinient. There exists a PC tool named My Avatar Editor running on Adobe Flash that can edit most information in a RCD file.
   * While unknown for sure, RCD most likely stands for **R**evolution **C**ore **D**ata, thanks to reverse engeneering efforts for the Switch Miis confirming the differences between StoreData and CoreData. .mii and .miigx are literal meanings (though the "gx" in .miigx is meant to represent the name of the Wii Homebrew application that imports those files onto the console, Save Game Loader GX), while .mae stands for **M**y **A**vatar **E**ditor.

* RSD
   * This format is identical to RCD, with one addition. There are two more bytes at the end of the file compared to RCD, which is the checksum. RSD files are commonly seen in the files of Wii games to store Wii-format Mii data files (though there are some rare instances of earlier titles that use RCD instead), and if one wishes to replace Miis, it's required to regenerate the checksum. A tool has been made for this named RSDmaker. Simply drag and drop your RCD file onto RSDmaker.exe and the checksum will be regenerated and your file will be renamed to include .rsd at the end.
   * RSD stands for **R**evolution **S**tore **D**ata, according to the September 2020 Nintendo leaks.

## Wii U/3DS formats

* CFSD (CFCD?)
   * This format is seen in 3DS titles to store Wii U/3DS-format Mii data files. It is identical to the FFSD format, though the fourth byte (known to store the console the Mii originates from) is set to `30`, as to identify the Mii as a 3DS Mii. This format is also used to store Miis inside of amiibo. Like RSD, there is a checksum at the end of the file. Instead of being placed directly at the end, however, there are first two `00` buffer bytes, *then* the checksum. The checksum is the same type as RSD. You can regenerate this checksum with RSDmakerU. Simply drag and drop your .cfsd file onto RSDmakerU.exe, and it will regenerate the checksum for you.
   * While unknown for sure, CFSD most likely stands for **C**TR **F**ace **S**tore **D**ata, thanks to reverse engeneering efforts for the Switch Miis confirming the differences between StoreData and CoreData.
      * This also implies the existence of a CFCD format (**C**TR **F**ace **C**ore **D**ata), though no official file currently exists with that extension. This theoretical CFCD format can be seen, however, in the 3DS's Mii database file. As expected, it's mostly the same as the regular CFSD format, just without the 2 byte checksum at the end of the file, and also without the 2 `00` byte buffer before that.

* FFSD (FFCD?)
   * This format is seen in Wii U titles to store Wii U/3DS-format Mii data files. It is identical to the CFSD format, though the fourth byte (known to store the console the Mii originates from) is set to `40`, as to identify the Mii as a Wii U Mii. (Note that Switch Miis converted to the Wii U/3DS-format also identify using `40`.) This format is also used to store Miis inside of amiibo. Like RSD, there is a checksum at the end of the file. Instead of being placed directly at the end, however, there are first two `00` buffer bytes, *then* the checksum. The checksum is the same type as RSD. You can regenerate this checksum with RSDmakerU. Simply drag and drop your .ffsd file onto RSDmakerU.exe, and it will regenerate the checksum for you.
   * While unknown for sure, FFSD most likely stands for Ca**f**é **F**ace **S**tore **D**ata, thanks to reverse engeneering efforts for the Switch Miis confirming the differences between StoreData and CoreData. The Wii U could not use the first letter of Café, as that would collide with the 3DS's name, which is also CFSD. So, to separate them, the Wii U uses the F in Café.
      * This also implies the existence of a FFCD format (Ca**f**é **F**ace **C**ore **D**ata), though no official file currently exists with that extension. This theoretical FFCD format can be seen, however, in the Wii U's Mii database file. As expected, it's mostly the same as the regular FFSD format, just without the 2 byte checksum at the end of the file, and also without the 2 `00` byte buffer before that.

## Switch formats

* NFSD (SwitchDB)
   * This format is seen to store SwitchDB-format Mii data files. The Nintendo Switch's Mii database file stored in NAND uses a different Mii format than those seen in Switch games. Thus, this format stores the former. This format actually stores two checksums. The first checksum is of the Mii data itself. The second one is of the Switch's console ID, meaning it should be the same across all Miis made on the same system. The NFSD format is the most compact Mii data file format, looking at an "amount of data stored" to "filesize" ratio.
   * The name NFSD is not official. There is currently no official file extension for this format. NFSD was a name created by myself, HEYimHeroic, and it stands for **N**X **F**ace **S**tore **D**ata.
      * There is somewhat of an official name, however. Internally, this format has been associated with "db" in examples such as "NFDB" and "sampledb" - this means that the name "SwitchDB" for the format might be pretty close to what it's actually called.
      * The usage of "NFIF" and "NFDB" does show that the "NFXX" style is present for the Switch. Thanks to reverse engeneering efforts for the Switch Miis confirming the differences between StoreData and CoreData, it's highly likely that the file extension for this format would indeed be NFSD. There would also be another theoretical format, NFCD, which can be seen in some specific instances. It, like other CoreData formats, does not contain the two checksums at the end of the file, and does not contain the Mii ID before that, shortening the file length even more.

* CHARINFO
   * This format is seen to store Switch-format Mii data files. The Nintendo Switch's Mii database file stored in NAND uses a different Mii format than those seen in Switch games. Thus, this format stores the latter. This format stores no checksums. The format appears to follow a similar structure to the NFSD format, while still separating its values into separate bytes, similar to the MNMS format.
   * Originally, it was believed Super Smash Bros. Ultimate was the only game to use the UFSD format, so at the time, it was unofficially named **U**ltimate **F**ace **S**tore **D**ata (UFSD), and was referred to as the Ultimate-format. Of course, we now know all Switch games use it, and it has since been renamed to the Switch-format, and since Miitopia (Switch Demo), we learned the official file extension is simply ".charinfo".

## Other formats

* MNMS
   * This format is only seen in a browser's Local Storage on Nintendo's official online Mii Studio website. If a change is made, the browser stores the Mii data in Local Storage, so if the user closes the window or refreshes, the site will be able to restore the changes the user was working on. However, we can use this to our advantage. A tool named the [Mii Studio Mii Loader](https://github.com/HEYimHeroic/MiiStudioMiiLoader) was written by myself, HEYimHeroic. It allows downloading and setting the browser's Local Storage at will, meaning we can import and export Miis via a string of HEX values. This string can be stored in a simple text file, or it can be saved directly to a file.
   * Of course, the Mii Studio does not save Mii data into files, and so no extension actually exists. The extension .mnms is an unofficial one standing for **M**y **N**intendo **M**ii **S**tudio.
