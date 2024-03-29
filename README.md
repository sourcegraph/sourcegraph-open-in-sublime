# Open in Sublime Sourcegraph extension

## ⚠️ Deprecation notice

**Sourcegraph extensions have been deprecated with the September 2022 Sourcegraph
release. [Learn more](https://docs.sourcegraph.com/extensions/deprecation).**

The repo and the docs below are kept to support older Sourcegraph versions.

## Description

Adds a button to the Sourcegraph's extension panel and at the top of files in code hosts like GitHub (when the Sourcegraph browser extension is installed) that will open the current file in Sublime Text.

**This extension requires all git repos to be cloned and available on your local machine.**

<picture>
<source srcset="https://user-images.githubusercontent.com/37420160/96816775-e9760400-13eb-11eb-812f-85046bd4db6d.png" width="100%" media="(prefers-color-scheme: dark)" />
<source srcset="https://user-images.githubusercontent.com/37420160/96816847-0ad6f000-13ec-11eb-9ef8-b1c3b2009a4d.png" width="100%" media="(prefers-color-scheme: light)" />
<img src="https://user-images.githubusercontent.com/37420160/96816847-0ad6f000-13ec-11eb-9ef8-b1c3b2009a4d.png" width="100%" alt="Screenshot" />
</picture>


## Prerequisites

- This extension requires all git repos to be cloned and available on your local machine.

- Sublime Text requires a URL handler installed such as [this one for macOS](https://github.com/inopinatus/sublime_url).

## Configurations

- `openInSublime.basePath`: [REQUIRED] String. The absolute path on your computer where your git repositories live. The extension will try to open the file in a clone named by the last segment of the repository name in that folder. 
  - This extension requires all git repos to be already cloned under this path with their original names, which the final path can later be altered using the `openInSublime.replacements` option.
  - `"/Users/yourusername/src"` is a valid absolute path, while `"~/src"` is not.

- `openInSublime.replacements`: [OPTIONAL] Object. Set to an object that includes pairs of strings, where each key will be replaced by its value in the final url. The key can be a string or a RegExp, and the value must be a string. 
  - Example: using `"openInSublime.replacements": {"(?<=Documents\/)(.*[\\\/])": "sourcegraph-$1"}` will add `sourcegraph-` in front of the string that matches the `(?<=Documents\/)(.*[\\\/])` RegExp pattern, while `"openInSublime.replacements": {"sourcegraph-": ""}` will remove `sourcegraph-` from the final URL.

- `openInSublime.osPaths`: [OPTIONAL] Object. The extension uses the assigned path for the detected Operating System when available. If no platform is detected then we will keep using the basePath provided with `openInSublime.basePath`. 
  - Note: Currently support `"windows"`, `"mac"`, and `"linux"` as keys.

## Examples

### Mac

**Requires a URL handler installed such as [this one for macOS](https://github.com/inopinatus/sublime_url).**

Opens repository files in your Documents directory:

```json
{
  "extensions": {
    "sourcegraph/open-in-sublime": true,
  },
  // where the cloned git repositories are located
  "openInSublime.basePath": "/Users/USERNAME/Documents/"
}
```

### Set basePath for multiple platforms

**Requires a URL handler installed such as [this one for macOS](https://github.com/inopinatus/sublime_url).**

Uses the assigned path for the detected Operating System when available:

```json
{
  "extensions": {
    "sourcegraph/open-in-sublime": true,
  },
  "openInSublime.osPaths": {
    "windows": "/C:/Users/USERNAME/folder/",
    "mac": "/Users/USERNAME/folder/",
    "linux": "/home/USERNAME/folder/"
  },
  // set basePath as fallback path when no operating system is detected
  "openInSublime.basePath": "/Users/USERNAME/Documents/"
}
```

## Development

1. Run `yarn && yarn run serve` and keep the Parcel bundler process running
1. [Sideload the extension](https://docs.sourcegraph.com/extensions/authoring/local_development) (at the URL http://localhost:1234 by default) on your Sourcegraph instance or Sourcegraph.com

When you edit a source file in your editor, Parcel will recompile the extension. Reload the Sourcegraph web page to use the updated extension.
