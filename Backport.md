Status of backports from forks 

|  |    |
|--|:--:|
| 🚫 | Can not be applied | 
| ☑️ | Ported or already done |
| ❔ | Not added could maybe be useful | 
| ❓ | Not sure if added needs to be checked | 
| 🔥 | Not ported but should be |
| 🚧 | Port Open |

| STATUS | Description  | FORK PR | Our PR / Notes | 
|:--------:|:-------|:------|:--|
|🚧| Explicit memory ownership in SocketMultiPlexer | https://github.com/debauchee/barrier/pull/411 |https://github.com/deskflow/deskflow/pull/8680 |
|🔥| Fix Inf Loop on fast TCP connections | https://github.com/debauchee/barrier/pull/557/files|  Requires barrier#411 first|
|🔥| Added nextScreen function | https://github.com/debauchee/barrier/pull/703 | requested by a few users| 
|🔥| EventTarget Type in place of void* for events | https://github.com/input-leap/input-leap/pull/1587 | | 
|🔥| smart pointers | https://github.com/input-leap/input-leap/pull/1574 https://github.com/input-leap/input-leap/pull/1578 https://github.com/input-leap/input-leap/pull/1588 ||
|❔| PreserveFocus Fix| https://github.com/debauchee/barrier/pull/178 | |
|❔| Fix Cpu Spike on win 10 | https://github.com/debauchee/barrier/pull/656| |
|❔| Revert make connection success a "note" | https://github.com/debauchee/barrier/pull/738| | 
|❔| Gui Status Log Comment about CLOG_PRINT, we should check if we have this issue | https://github.com/debauchee/barrier/pull/739| |
|❔| remove unused defines | https://github.com/debauchee/barrier/pull/981 | | 
|❔| only active client can grab clipboard | https://github.com/input-leap/input-leap/pull/1434 |  |
|❓| Support sun keys | https://github.com/debauchee/barrier/pull/790 | |
|❓| Suppoet Kan, Eisu_toggle and Muhenkan| https://github.com/debauchee/barrier/pull/832 | |
|❓| Hscroll fix | https://github.com/debauchee/barrier/pull/391 | |
|❓| noexcept | https://github.com/debauchee/barrier/pull/718 | |
|❓| Add hotkey config rule for `,` and `;` | https://github.com/debauchee/barrier/pull/916 | should fix: https://github.com/deskflow/deskflow/issues/7130 |
|❓| Use Ansi code page for multibyteString | https://github.com/debauchee/barrier/pull/979 | could help with some localization issue internally 
|❓| Simplify code path with lots of ifdef removals | https://github.com/input-leap/input-leap/pull/1491 | |
|☑️| IPv6 Support | https://github.com/debauchee/barrier/pull/19 |  |
|☑️| Scroll fix (osx) | https://github.com/debauchee/barrier/pull/64 | |
|☑️| Scroll fix (x11) | https://github.com/debauchee/barrier/pull/68 | |
|☑️| Fix Data fromUtf8| https://github.com/debauchee/barrier/pull/121 | https://github.com/deskflow/deskflow/pull/6617
|☑️| Modifier fix (Osx)| https://github.com/debauchee/barrier/pull/210 | |
|☑️| Gui: Rename "apply" => "restart" | https://github.com/debauchee/barrier/pull/292 | https://github.com/deskflow/deskflow/pull/8650 |
|☑️| macOS config file errors |https://github.com/debauchee/barrier/pull/336| |
|☑️| Fix international Quote | https://github.com/debauchee/barrier/pull/359 | |
|☑️| Fix ssl leak on shutdown | https://github.com/debauchee/barrier/pull/408 | |
|☑️| Elevate XSOcketAdderssInUse to Error | https://github.com/debauchee/barrier/pull/655 |
|☑️| Fix RetryTimer | https://github.com/debauchee/barrier/pull/409 | https://github.com/deskflow/deskflow/pull/6077 |
|☑️| Fix MouseDrift | https://github.com/debauchee/barrier/pull/424 | https://github.com/deskflow/deskflow/pull/6469 |
|☑️| use std::string | https://github.com/debauchee/barrier/pull/709 | https://github.com/deskflow/deskflow/pull/8048|
|☑️| use std::string | https://github.com/debauchee/barrier/pull/710 | https://github.com/deskflow/deskflow/pull/8048|
|☑️| use std::string | https://github.com/debauchee/barrier/pull/711 | https://github.com/deskflow/deskflow/pull/8048|
|☑️| use std::string | https://github.com/debauchee/barrier/pull/713 | https://github.com/deskflow/deskflow/pull/8048|
|☑️| use std::string | https://github.com/debauchee/barrier/pull/714 | https://github.com/deskflow/deskflow/pull/8048|
|☑️| use std::string | https://github.com/debauchee/barrier/pull/715 | https://github.com/deskflow/deskflow/pull/8048|
|☑️| use std::string | https://github.com/debauchee/barrier/pull/716 | https://github.com/deskflow/deskflow/pull/8048|
|☑️| use std::string | https://github.com/debauchee/barrier/pull/717 | https://github.com/deskflow/deskflow/pull/8048|
|☑️| use std::string | https://github.com/debauchee/barrier/pull/718 | https://github.com/deskflow/deskflow/pull/8048|
|☑️| Make connection success a "note" |https://github.com/debauchee/barrier/pull/725| |
|☑️| XWindow event stutter | https://github.com/debauchee/barrier/pull/679 | https://github.com/deskflow/deskflow/issues/6693|
|☑️| enum class for  config items | https://github.com/debauchee/barrier/pull/708| |
|☑️| Include version info in windows exe | https://github.com/debauchee/barrier/pull/978 | |
|☑️| Clenaup S,U int types for std int sizes | https://github.com/debauchee/barrier/pull/1349 | |
|☑️| Enable crypto by default | https://github.com/debauchee/barrier/pull/1342 | | 
|☑️| Support SHA256 | https://github.com/debauchee/barrier/pull/1343 |https://github.com/deskflow/deskflow/pull/8152 | 
|☑️| Fix CVE-2021-42072, CVE-2024-42073 | https://github.com/debauchee/barrier/pull/1351 |https://github.com/deskflow/deskflow/pull/7931 | 
|☑️| Fix CVE-2021-42074 | https://github.com/debauchee/barrier/pull/1351 |https://github.com/deskflow/deskflow/pull/7982 | 
|☑️| Fix CVE-2021-42075 | https://github.com/debauchee/barrier/pull/1350 |https://github.com/deskflow/deskflow/pull/7981 | 
|☑️| Fix CVE-2021-42076 | https://github.com/debauchee/barrier/pull/1347 |https://github.com/deskflow/deskflow/pull/7984 |
|☑️| use std::genenv | https://github.com/debauchee/barrier/pull/847/ | Can't port directly but should do similar, https://github.com/deskflow/deskflow/pull/8678 |
|☑️| remove --no-xinitthreds option | https://github.com/input-leap/input-leap/pull/1503  and https://github.com/input-leap/input-leap/pull/1504 | https://github.com/deskflow/deskflow/pull/8679 |
|☑️| TcpSocket Handle RW at same time | https://github.com/debauchee/barrier/pull/211 | https://github.com/deskflow/deskflow/pull/8675 |
|☑️| More std::mutex | https://github.com/debauchee/barrier/pull/410 | https://github.com/deskflow/deskflow/pull/8674 |
|☑️| Use std::this_thread::sleep to replace ARCH_SLEEP | https://github.com/input-leap/input-leap/pull/1462 && https://github.com/input-leap/input-leap/pull/1499| https://github.com/deskflow/deskflow/pull/8677 | 
|☑️| Use std::crono items to replace ARCH_TIME | https://github.com/input-leap/input-leap/pull/1464 | https://github.com/deskflow/deskflow/pull/8637 | 
|☑️| std::function | https://github.com/input-leap/input-leap/pull/1552 |https://github.com/deskflow/deskflow/pull/8697 |