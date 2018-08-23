**Dvorak for Programmers with European Keys**
==============================================

This is the usual **Dvorak for Programmers** keyboard layout (initially made by Ronald Kaufmann) upgraded to include European characters as alternative symbols. The way they match the main letters was inspired by [EurKEY](https://eurkey.steffen.bruentjen.eu) layout (by Steffen Bruentjen). Other special characters distributed among the keys in a *reasonable* way (in my own way of understanding of what *reasonable* is, although feedback is always appreciated). Essential dead keys are present for common diactricts (marked red on the image below), but they are located on the most distant keys to reduce the chance of influence on hotkeys.

![Dvorak for Programmers with European Keys](preview.png)

### Manual installation on (Ubuntu) Linux

All the actions below are to be performed under **#root**

```sh
$ sudo su
```

- insert the contents of the [us-dpe](https://raw.githubusercontent.com/asvd/programmer-dvorak-eu/master/us-dpe) layout at the very end of `/usr/share/X11/xkb/symbols/us`

- open `/usr/share/X11/xkb/rules/evdev.xml` and find the `us` layout configuration starting with something like

 ```xml
 <layout>
   <configItem>
     <name>us</name>

     <shortDescription>en</shortDescription>
     <description>English (US)</description>
     <languageList>
       <iso639Id>eng</iso639Id>
     </languageList>
   </configItem>
 ```

- in the beginning of the `<variantList>` below the layout header, insert the variant configuration for the new layout:

 ```xml
 <variant>
   <configItem>
     <name>dpe</name>
     <description>English (Programmer Dvorak Eur. Keys)</description>
   </configItem>
 </variant>
 ```

- delete xkb cache:

 ```
 # rm /var/lib/xkb/*.xkm
 ```
or

 ```
 # dpkg-reconfigure xkb-data
 ```

Now the new layout should be selectable in the system settings window as a variant of English layout


---

visit my homepage: https://asvd.github.io

follow me on twitter: https://twitter.com/asvd0
