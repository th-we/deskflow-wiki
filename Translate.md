# Guide for translators

This is a general guide for Translating deskflow. Those looking to update in application translaions should install Qt Linguist. For translators who do no have Qt (dev tools ) installed you can install a standalone version of linguist.

 - Linux you can get this from your distros package manager
 - On Mac os you can install this with brew
 - Window uses can download a binary from the Qt6 version of linguist [here](https://github.com/thurask/Qt-Linguist/)

Not all items that need translation are in ts files. Some distributed files can have translations included direclty in them see the [Translating non text files](#translating-non-code-files) section for more info on these types (may not be a complete list at this time)

## Adding A New Translations for deskflow 

###  Add the translation to list in `translations/CMakeLists.txt`
  - Look for `set (${CMAKE_PROJECT_NAME}_TRS` in `translations/CMakeLists.txt`. add your new item in the list after it. This variable controls what ts files are generated.
  - Language file names should be `${CMAKE_PROJECT_NAME}_LANG.ts` where LANG is the ISO639 name for your language (en, es, fr, it, ko, etc). For Portuguese and Chinese you must also include the country code ie (pt_BR, pt_PT, zh_CN and zh_TW)
  - The Lang will also be used to attempt to deploy a matching Qt translation file (on windows / mac os) 
  - If we were adding Chinese (China) and Italian we would add the following lines to the cmake file 
    - `${CMAKE_PROJECT_NAME}_zh_CN.ts` (Chinese (china))
    - `${CMAKE_PROJECT_NAME}_it.ts` (Italian)

```
set (${CMAKE_PROJECT_NAME}_TRS
  ${CMAKE_PROJECT_NAME}_es.ts  # Spanish
  ${CMAKE_PROJECT_NAME}_it.ts  # Italian
  ${CMAKE_PROJECT_NAME}_zh_CN.ts # Chinese (China)
)
```

 1. Run Cmake and build the project to generate the new TS files in the translations directory
 1. After generating a new language file you MUST translate the "LocalizedName" in the I18N Section string before using the translation.

## Updating existing TS files

 - Translations sources are updated when the project is built.
 - In order to update the translations in a TS file you should use Qt Linguist. Check the [Qt Translator Guide](https://doc.qt.io/qt-6/linguist-translators.html) for general info about using Qt Linguist.  
 - the place holders `%1` `%2` (%Some_Number) can be moved around and will be replaced by a string
 - the place holder `%n` will be replaced by a number and is optional to have in the translated string
 - the modifier `&` is used to define an accelerator. For example &Close will have the C accelerated (i.e Alt+C will select the item). Adjust these when translating so they make sense in the target language.


## Translating Non code files

In addition to the ts files several other files in the repo support direct translations with the file

### Desktop files

translations can be added to  the desktop file `deploy/linux/org.deskflow.deskflow.desktop`

you can add to the desktop file `Name[langcode]` and `Description[langcode]`  entries

ex for spanish add

Name[es]= Spanish Name of Deskflow
Description[es]=Spanish Description of deskflow

More info https://specifications.freedesktop.org/desktop-entry-spec/latest/localized-keys.html

### Translating appstream data

in the appstream data translations can also be added `deploy/linux/org.deskflow.deskflow.metainfo.xml`

you can add 
`xml:lang="es"` to make new description , keywords 

More info https://freedesktop.org/software/appstream/docs/chap-Metadata.html#tag-description

