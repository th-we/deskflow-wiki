# Guide for translators

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
 - the place holders `%1` can be moved around and will be replaced by a string
 - the place holder `%n` will be replaced by a number and is optional to have in the translated string
 - the modifier `&` is used to define an accelerator. For example &Close will have the C accelerated (i.e Alt+C will select the item). Adjust these when translating so they make sense in the target language.





