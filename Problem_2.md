## Problem 2
### Creating directory

Q2(a). Create a directory without name from command line <br>
A. We can't have a directory/file with an empty name. However, the name can be something we can't see like whitespace or control characters. We can do this by mkdir " " . It will look like that the folder has no name.


Q2(b). Create a directory with name "-okgoogle" <br>
A. Tried running mkdir -okgoogle. Got invalid option -- 'o'. The reason I found was it treats anything after (-) as an option. -o is used to write output to files. But there is no such option. Hence error. There are 2 options for creating files with this kind of name.<br>
`mkdir ./-okgoogle`
`mkdir -- -okgoogle`
