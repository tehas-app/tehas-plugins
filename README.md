# tehas-plugins

The list of plugins the tehas maintainers build and vet, in
[`plugins.json`](plugins.json).

A plugin adds a feature to a [tehas](https://tehas.app) factory without
changing core: a view in the dashboard, a check on a pull request, a skill
for the chats. How plugins work, and every grant they can ask for, is on
[the plugins page](https://tehas.app/plugins).

## Before you build or fork

1. **Look here first.** If a plugin in the list does the job, use it.
2. **Build a plugin** if none does. Start from [the plugins
   page](https://tehas.app/plugins), and check the manifest with
   `tehas plugin check <dir>`. A plugin may use any licence.
3. **Ask for a surface** if your plugin needs something tehas does not
   offer: a "Plugin surface request" in
   [tehas](https://github.com/tehas-app/tehas/issues/new?template=plugin-surface.yml)
   for what a factory offers, or in
   [tehas-industry](https://github.com/tehas-app/tehas-industry/issues/new?template=plugin-surface.yml)
   for what industry and Obeya offer.

Do not fork tehas, and do not patch core, to get a feature a plugin can
give.

## What "vetted" means

A plugin is listed as `vetted` at one commit, when:

- the tehas maintainers wrote it, or read every line of that commit;
- its manifest passes `tehas plugin check`, and every grant it asks for is
  one a person can weigh in `tehas plugin review`;
- its image builds from that commit with no network, its base images pinned
  by digest;
- it ran on a factory host at that commit, under its grants.

A new commit is not vetted until it is checked again. Grants are given for a
commit, so a factory that pins the vetted commit gets what was vetted.

`building` means the plugin is written and its tests pass, but it has not
run on a host: no plugin runs before tehas 2.1.

## Not a submission queue

This list holds the maintainers' own plugins. It takes no pull requests
that add a plugin. Plugins anyone else writes work the same way; they are
just not listed here. Nothing about the list is automatic: each entry is
added by a maintainer, by hand.

## The fields

| Field | Meaning |
| --- | --- |
| `name` | The plugin's name, as in its manifest and in `TEHAS_PLUGINS` |
| `about` | What it does, in one line |
| `repo` | Its repository, or `null` while it is not public |
| `asks` | The grants its manifest asks for |
| `model` | Whether it uses the factory's model |
| `needs` | The releases it needs: `tehas`, and `industry` or `obeya` when it draws in their pages |
| `state` | `building` or `vetted` |
| `vetted` | For a vetted plugin: `{"commit", "manifest_sha256", "at", "by"}`. Pin this commit |
