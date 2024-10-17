I want to contribute the open-source note repository: https://forms.gle/TeQUktn7GB3wyg6D6

# How to use this notes library?

<p align="center">
  <a href="./README.md">简体中文</a> |
  <a href="./README_en.md">English</a>
</p>

## Non-technical personnel

```mermaid
---
title: Non-technical personnel
---
flowchart TB
open-notes-repo-by-obsidian[Open notes repository with Obsidian]
download-notes-repository[Download notes repository]

download-notes-repository --> Unzip --> open-notes-repo-by-obsidian
```

Download notes library.

![[2024-10-11-img-6-how-to-use-this-notes-repo?-download-notes-repo-as-zip.png]]
![2024-10-11-img-6-how-to-use-this-notes-repo?-download-notes-repo-as-zip.png](./4.1%20附件/2024-10-11-img-6-how-to-use-this-notes-repo%3F-download-notes-repo-as-zip.png)

Unzip then open your notes repo by Obsidian.

![[2024-10-11-img-4-how-to-use-this-notes-repo?-open-your-notes-repo.png]]
![2024-10-11-img-4-how-to-use-this-notes-repo?-open-your-notes-repo.png](./4.1%20附件/2024-10-11-img-4-how-to-use-this-notes-repo%3F-open-your-notes-repo.png)

You can use iCloud, Google Drive or Microsoft oneDrive to sync your notes among your devices.

> Sync with GitHub  
> If you want to sync with GitHub, please ensure you have install Git and generate SSH key for your GitHub account.
> See the instruction with GitHub below.

## Technical personnel

```mermaid
---
title: Technical personnel
---
flowchart TB
download-git[Download Git]
generate-ssh[Generate ssh key]
register-github[Register GitHub account]
config-ssh[Configure ssh for GitHub account]
fork-notes-repo[Fork notes repository]
clone-notes-repo[Clone notes repository to local computer]
open-notes-repo-by-obsidian[Open notes repository with Obsidian]
write-notes[Write notes]
sync-by-git[Sync notes using git]
get-latest-repository-changes[Get latest repository changes]

register-github & generate-ssh --> config-ssh --> fork-notes-repo --> clone-notes-repo
download-git --> clone-notes-repo --> open-notes-repo-by-obsidian --> write-notes --> sync-by-git --> get-latest-repository-changes
```

Fork the notes repository to your GitHub account.

![[2024-10-11-img-1-how-to-use-this-notes-repo?-repo.png]]
![2024-10-11-img-1-how-to-use-this-notes-repo?-repo.png](./4.1%20附件/2024-10-11-img-1-how-to-use-this-notes-repo%3F-repo.png)

![[2024-10-11-img-2-how-to-use-this-notes-repo?-fork.png]]
![2024-10-11-img-2-how to use this notes repo?-fork.png](./4.1%20附件/2024-10-11-img-2-how-to-use-this-notes-repo%3F-fork.png)

![[2024-10-11-img-3-how-to-use-this-notes-repo?-clone you own notes repo.png]]
![2024-10-11-img-3-how to use this notes repo?-clone you own notes repo.png](./4.1%20附件/2024-10-11-img-3-how-to-use-this-notes-repo%3F-clone%20you%20own%20notes%20repo.png)

```bash
git clone <ssh_github_link>
```

Then open your notes repo by Obsidian.

![[2024-10-11-img-4-how-to-use-this-notes-repo?-open-your-notes-repo.png]]
![2024-10-11-img-4-how-to-use-this-notes-repo?-open-your-notes-repo.png](./4.1%20附件/2024-10-11-img-4-how-to-use-this-notes-repo%3F-open-your-notes-repo.png)

You can save your notes on GitHub directly, try to use the command(`Cmd + p` to open Command palette) in Obsidian.

![[2024-10-11-img-5-how-to-use-this-notes-repo?-commit-and-sync-with-Git.png]]
![2024-10-11-img-5-how to use this notes repo?-commit-and-sync-with-Git.png](./4.1%20附件/2024-10-11-img-5-how-to-use-this-notes-repo%3F-commit-and-sync-with-Git.png)

Please read [[2024-10-09-Note management-How to manage work notes ?]] [link (please use Obsidian to view this link)](./2024-10-09-Note%20management-How%20to%20manage%20work%20notes%20%3F.md) first before write your first note.
