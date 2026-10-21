# Scene Labs plugins

Claude Code and Codex skills for authoring animated Scene diagrams: Mermaid and PlantUML sequence diagrams, Mermaid flowcharts, and Mermaid state diagrams.

## Install in Claude Code

Run these commands in Claude Code:

```text
/plugin marketplace add scene-labs/scene-plugins
/plugin install scene@scene-labs
```

Choose user scope to use the plugin across projects.

## Enable automatic updates

Open `/plugin`, select **Marketplaces → scene-labs → Enable auto-update**.
Third-party marketplaces have auto-update disabled by default; installing the plugin does not enable it.

Claude Code checks enabled marketplaces after a session starts. New versions load in the next session, or run `/reload-plugins` after an update to apply it in the current session.

To update manually from your terminal:

```sh
claude plugin update scene@scene-labs
```

## Install in Codex

With a recent Codex CLI, run these commands in your terminal:

```sh
codex plugin marketplace add scene-labs/scene-plugins
codex plugin add scene@scene-labs
```

Start a new Codex session and ask it to create a Scene diagram using the Scene plugin. In the ChatGPT desktop app, restart the app and look for Scene under the Scene Labs source in the Plugins Directory.

### Update in Codex

Refresh the marketplace and install the current plugin, then start a new session:

```sh
codex plugin marketplace upgrade scene-labs
codex plugin add scene@scene-labs
```

Codex's documented Git-marketplace workflow does not provide Claude Code's **Enable auto-update** switch. These commands provide an explicit update path; installing this package does not configure a background updater.

## Use

Ask Claude to create a Scene diagram or add Scene annotations to an existing diagram. You can also invoke the skill explicitly:

```text
/scene:scene Describe your system interaction here
```

The skill teaches Claude Scene's annotations and playback behavior. It does not install or run the Scene viewer.

If you previously copied a standalone Scene skill into your Claude skills directory, remove that old copy after confirming the plugin works so you do not keep loading outdated instructions.

## Publish an update

1. Update `plugins/scene/skills/scene/SKILL.md` from the current Scene authoring reference.
2. Bump `version` together in `plugins/scene/plugin.json` and `plugins/scene/.claude-plugin/plugin.json`. The portable manifest serves Codex; the Claude manifest serves Claude Code. Do not put a second version in either marketplace catalog. Claude users do not receive changed files without a version bump.
3. Validate both the plugin and marketplace:

   ```sh
   claude plugin validate ./plugins/scene
   claude plugin validate .
   ```

4. Check Codex discovery with `codex plugin list --marketplace scene-labs --available --json` from this repository.
5. Review the changes and verify the skill loads in both clients before pushing to `main`.

Keep the published skill synchronized with the Scene docs and onboarding instructions when the syntax changes.

Use Scene Labs as both the git author and committer, with a non-personal email address. Do not copy personal repository history or include personal account links in published files.

See the [Claude Code plugin documentation](https://code.claude.com/docs/en/discover-plugins) for installation and updates.

## License

MIT. See [LICENSE](LICENSE).
