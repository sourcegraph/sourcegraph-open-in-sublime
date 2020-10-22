# Open in Sublime (Sourcegraph extension)

Adds a button at the top of files in both Sourcegraph app and code hosts like GitHub (when the Sourcegraph browser extension is installed) that will open the current file in Sublime Text.

<picture>
<source srcset="https://user-images.githubusercontent.com/37420160/96816775-e9760400-13eb-11eb-812f-85046bd4db6d.png" media="(prefers-color-scheme: dark)" />
<source srcset="https://user-images.githubusercontent.com/37420160/96816847-0ad6f000-13ec-11eb-9ef8-b1c3b2009a4d.png" media="(prefers-color-scheme: light)" />
<img src="https://user-images.githubusercontent.com/37420160/96816847-0ad6f000-13ec-11eb-9ef8-b1c3b2009a4d.png" alt="Screenshot" />
</picture>

## Settings

- `openInSublime.basePath`: The absolute path on your computer where your git repositories live. This extension requires all git repos to be already cloned under this path with their original names. `"/Users/yourusername/src"` is a valid absolute path, while `"~/src"` is not.

Sublime Text requires a URL handler installed such as [this one for macOS](https://github.com/inopinatus/sublime_url).
