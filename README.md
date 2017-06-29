# rewriteflac
Removes padding on FLAC files

### Setup metaflac in foobar2000
1. Download [metaflac][metaflac on xiph].
2. Extract the zip file and place metaflac.exe in `C:/METAFLAC/metaflac.exe`.
3. Download [foo_run][foobar run services].
4. Install the component in foobar.
5. Now, go to `File > Preference > Tools > Run services` and Add a new service.
6. Set the label as `Strip FLAC Images and Padding`.
7. Press the [...] button add metaflac.exe from `C:/METAFLAC/metaflac.exe`.
8. Add the paramenters ` --remove --block-type=PICTURE,PADDING --dont-use-padding "%path%"`
10. The end result should be  
    ```
    C:\METAFLAC\metaflac.exe --remove --block-type=PICTURE,PADDING --dont-use-padding "%path%"
    ```
11. Add nother new service for adding back 8KB of padding labeled as `Add FLAC Padding`.
    > There's one downside to using metaflac with the above method. The used command line options remove ALL padding from the FLAC files. This isn't necessarily an issue, but padding serves a purpose. If metadata gets added or changed on a file without any padding, even if it's just fixing a small typo in a title, the whole file needs to be re-written on the HDD. Depending on the amount of files you're editing, the file sizes (think about high resolution multi-channel stuff)  and speed of your drive, this may take longer than you'd expect.
    
    ```
    C:\METAFLAC\metaflac.exe --add-padding=8192 "%path%"
    ```

[metaflac on xiph]: https://xiph.org/flac/download.html
[foobar run services]: http://www.foobar2000.org/components/view/foo_run
