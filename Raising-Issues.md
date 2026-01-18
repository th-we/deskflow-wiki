> [!Important]
> If your having an issue. Always try the [continuous](https://github.com/deskflow/deskflow/releases/tag/continuous) version. Many bugs are 
fixed between releases and yours could be one of them.

> [!Note] 
> When providing version information use the copy button on the about dialog. This will include the version as well as the OS Type OS Version, Processor Architecture, and session type
 
If You have Found an issue not fixed by continuous

  Check the existing [issues](https://github.com/deskflow/deskflow/issues?q=is%3Aissue) to see if someone has reported the issue your experiencing. When searching include closed issues as they may regression or the issue is could be a misunderstanding.

If a matching or similar issues exists add a :+1:  to the issue. There is no need to comment unless your comment add new information to help solve the bug. An example of a useful comment could be your platform not matching the reporters if an issues is said to be on a specific platform only. We would like to keep the issues comments on topic and uncluttered as some issues can take some time and much discussion to resolve.

##### Creating new issues

 1. When in doubt start by [asking a question](https://github.com/deskflow/deskflow/discussions/new?category=q-a) 
 1. Enable debug level in your log to capture the log the next time the issue happens. 
 1. When reporting issues make sure you include the initial version tested as well as the version of the continuous used when testing.
 1. Include logs when reporting 
 1. Use `<details> <summary><h3>TITLE</h3></summary LONG BLOCK TEXT</details>` tags to wrap logs and other lengthy blocks so they are collapse-able  
 1. Fill out the bug form completely, when relevant include info about the both server and clients

### Maintainers should follow these rules when raising or triaging a new issue.

See also: [Hacking Guide](https://github.com/deskflow/deskflow/wiki/Hacking-Guide)

1. If an issue is OS-specific, use the OS tag ([`windows`](https://github.com/deskflow/deskflow/labels/windows), [`macos`](https://github.com/deskflow/deskflow/labels/macos), `linux`)
1. Move an issue out of [[triage|Triaging issues]]
1. Remove the [`stale`](https://github.com/deskflow/deskflow/labels/stale) label if an issue has new activity (and reopen the issue if closed)