# Guide for translators

This is a general guide for Translating Deskflow. Those looking to update in application translations should install Qt Linguist. For translators who do no have Qt (dev tools ) installed you can install a standalone version of linguist.

 - Linux you can get this from your distros package manager
 - On Mac os you can install this with brew
 - Window uses can download a binary from the Qt6 version of linguist [here](https://github.com/thurask/Qt-Linguist/)

Not all items that need translation are in ts files. Some distributed files can have translations included directly in them see the [Translating non code files](#translating-non-code-files) section for more info on these types (may not be a complete list at this time)

## Adding A New Translations for Deskflow 

###  Add the translation to list in `translations/CMakeLists.txt`
  - Look for `set (${CMAKE_PROJECT_NAME}_TRS` in `translations/CMakeLists.txt`. add your new item in the list after it. This variable controls what ts files are generated.
  - Language file names should be `${CMAKE_PROJECT_NAME}_LANG.ts` where LANG is the ISO639 name for your language (en, es, fr, it, ko, pt etc). For Brizilan Portuguese and Chinese you must also include the country code ie (pt_BR, zh_CN and zh_TW)
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
### Generate and Set the Localized Language Name.
 1. Run Cmake and build the project to generate the new TS files in the translations directory
 1. After generating a new language file you MUST translate the "LocalizedName" in the I18N Section string before using the translation.

### Update I18N Tests

 Update the `I18NTests` to include the new language in its `m_langMap` This map is used as basic sanity check your new entry will be 
a map of the "native name" and the 639 name ex: for Italian `{QStringLiteral("Italiano"), QStringLiteral("it")}` 
## Updating existing TS files

### Translation notes

 - Translations sources are updated when the project is built.
 - In order to update the translations in a TS file you should use Qt Linguist. Check the [Qt Translator Guide](https://doc.qt.io/qt-6/linguist-translators.html) for general info about using Qt Linguist.  

### Translating Placeholders and accelerators
#### Numeric placeholder

The placeholder `%n` is replaced by a number. When used to translate plural forms using `%n` in the translated string is optional. `%n` will be replaced by a number at runtime.

For example the input string `you have %n message(s)` 

The single form would be `you have a message` with a plural form of `you have %n messages`

#### String Placeholders

The placeholder `%number>0` (i.e `%1`, `%2`, ...) will be replaced by a string at runtime. The strings comments should tell you what the each one will be replaced by. When translating the order of these placeholders can be changes as long as all of the used placeholders exists in the translated string. 

For Example the input string `There is a %1 in the %2`  (%1 is a animal Name , %2 is a Place)
 
Could be translated as `You look %2 and can see the %1` 

#### Accelerators and shortcuts

Shortcuts `Ctrl+X` are expected to be translated. the modifier `&` is used to define an accelerator. For example &Close will have the C accelerated (i.e Alt+C will select the item). Adjust these when translating so they make sense in the target language.

### Testing translations

You can test new and updated translation files without rebuilding or restarting deskflow. In order to test your new translations you need to `release` it from Qt Linguist. This will create a `*.qm` file this file will need to be placed in the deskflow translation directory 

`C:\Program Files\Deskflow\translations` on windows

`Deskflow.app/Contents/Macos/translations/` Mac bundle

`<installPrefix>/share/deskflow/translations` Linux

The `<installPrefix>` for linux is usually 
 - `/usr` Most system installed packages
 - `/var/app/org.deskflow.Deskflow/data` Flatpak, System installed
 - `~/.var/app/org.deskflow.Deskflow/data` Flatpak, User installed

After copying the new file you should be able to see the language next time you enter the settings screen. 

## Translating Non code files

In addition to the ts files several other files in the repo support direct translations with the file

### Desktop files

translations can be added to  the desktop file `deploy/linux/org.deskflow.deskflow.desktop`

you can add to the desktop file `Name[langcode]` and `Description[langcode]`  entries

ex for Spanish add

Name[es]= Spanish Name of Deskflow
Description[es]=Spanish Description of Deskflow

More info https://specifications.freedesktop.org/desktop-entry-spec/latest/localized-keys.html

### Translating appstream data

in the appstream data translations can also be added `deploy/linux/org.deskflow.deskflow.metainfo.xml`

you can add 
`xml:lang="es"` to make new description , keywords 

More info https://freedesktop.org/software/appstream/docs/chap-Metadata.html#tag-description

