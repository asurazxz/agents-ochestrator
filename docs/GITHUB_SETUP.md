# GitHub repository preparation

Status: guidance only. Repository creation, connection, commits, and publishing are separate follow-up work.

## Suggested creation settings

- Name: `agents-orchestrator` (correct spelling; the local folder has not been renamed).
- Description: `Self-hosted shared project context for teams using AI coding agents.`
- Visibility: Public for open-source development, or Private temporarily while preparing a release.
- Create an empty repository: do not initialize a README, `.gitignore`, or license through the creation form. Local documentation and ignore files already exist.

GitHub recommends avoiding initial generated files when [importing existing local code](https://docs.github.com/en/migrations/importing-source-code/using-the-command-line-to-import-source-code/adding-locally-hosted-code-to-github?platform=linux).

## License choice

The specific license remains undecided. MIT is a simple permissive option to consider, not an accepted project decision. Select and add a license before describing a release as open-source; [GitHub explains](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/licensing-a-repository) that public visibility alone does not grant general reuse rights. Do not import competitor code without reviewing its actual license and attribution requirements.

## Separate this project from the parent repository

At the time of this documentation update, the folder belongs to a larger existing `Personal` Git repository. The new repository should contain only this project's files and an independent history.

Once the new URL is available, establish a dedicated checkout in a separate follow-up. Copy only the intended project files; exclude parent Git metadata, environment secrets, caches, and guarded machine-specific directories. Preserve the surrounding repository and its remote. Do not push the parent's history or use a broad staging command that collects unrelated files.

Do not initialize a nested repository or replace the parent remote as part of this documentation task. The final checkout location and connection will be handled when the new URL and workspace are available.

## Before the first public release

- Resolve the license and check dependency licenses when code exists.
- Describe current functionality honestly; this is presently a documentation scaffold.
- Keep private network addresses, credentials, and personal transcripts out of the repository.
- Provide reproducible installation and upgrade instructions when the application is implemented.
- Document supported agent versions and actual compatibility results.
- Add relevant automation and contribution guidance as implementation progresses.

No application, network, deployment, or Git configuration changes have been made by this documentation update.
