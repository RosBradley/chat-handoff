# Building and releasing

## Local build

Run validation, tests and scripts/build.py from README.md. The output directory
contains only chat-handoff-for-chatgpt.zip and SHA256SUMS.txt. The checksum
file contains one entry for that plugin ZIP. Archives use fixed metadata and
sorted entries for repeatable bytes.

The plugin contains only the manifests, skill and license/notice. It excludes
local handoffs, generated installations, Git internals and secrets. Developers
can clone the repository or use GitHub's automatic source downloads.

## Version

Update plugin.json, .codex-plugin/plugin.json, the skill Version line and
CHANGELOG.md together. The Claude and Microsoft Copilot skills in this
repository share the same version number, so a new version changes theirs too. The root plugin name remains chat-handoff-for-chatgpt. Release
versions currently use stable major.minor.patch strings.

An existing account plugin is a separate deployment. Building this source does
not update it; use its existing identity and current-release guard when an
update is requested. Do not create a duplicate account plugin for every release.

## GitHub workflows

The source repository is
[RosBradley/chat-handoff](https://github.com/RosBradley/chat-handoff).
Its downloads are on the
[Releases page](https://github.com/RosBradley/chat-handoff/releases): one
release per version, tagged `v<version>`, with a download for each of the
repository's skills. The plugin ZIP is the installation download for ordinary
ChatGPT users and already includes the skill. SHA256SUMS.txt stays a local
build output; the release page shows each download's SHA-256. GitHub
also displays automatic Source code downloads; these are for developers.

The release workflow names the plugin ZIP explicitly so older archives left in
a local output directory cannot be uploaded accidentally.

CI (.github/workflows/chatgpt-ci.yml) runs validation, unit tests and builds on
pushes and pull requests that touch chatgpt/. The release workflow
(.github/workflows/release.yml) runs when a version changes on main. It checks
that all three skills have the same version, validates, tests and builds, then
publishes `v<version>` unless that release already exists. Change the version
only when ready to publish. Every release link in the docs must name the
current version, or the release stops.

The release job publishes build artifacts using the repository's GitHub token.
Repository policies may require enabling Actions or granting release permissions.
Hosted validation and release workflows passed for v1.1.5 in the old repository. Verify the workflow
results and uploaded assets for every future release.

## Public plugin directory

A GitHub release is not a public OpenAI plugin-directory submission. This
repository does not supply verified public listing URLs, support policy,
privacy policy, branding or submission approval. Complete that separate
process if public directory publication is requested.
