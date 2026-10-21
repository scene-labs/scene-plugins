# Scene Labs plugins

Claude Code skills for authoring animated Scene diagrams: Mermaid and PlantUML sequence diagrams, Mermaid flowcharts, and Mermaid state diagrams.

## Install

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

## Use

Ask Claude to create a Scene diagram or add Scene annotations to an existing diagram. You can also invoke the skill explicitly:

```text
/scene:scene Describe your system interaction here
```

The skill teaches Claude Scene's annotations and playback behavior. It does not install or run the Scene viewer.

If you previously copied a standalone Scene skill into your Claude skills directory, remove that old copy after confirming the plugin works so you do not keep loading outdated instructions.

## Publish an update

1. Update `plugins/scene/skills/scene/SKILL.md` from the current Scene authoring reference.
2. Bump `version` in `plugins/scene/.claude-plugin/plugin.json`. Keep the version only in this manifest: commits without a version change do not update installed copies.
3. Validate both the plugin and marketplace:

   ```sh
   claude plugin validate ./plugins/scene
   claude plugin validate .
   ```

4. Review the changes and verify the skill loads before pushing to `main`.

Keep the published skill synchronized with the Scene docs and onboarding instructions when the syntax changes.

Use Scene Labs as both the git author and committer, with a non-personal email address. Do not copy personal repository history or include personal account links in published files.

See the [Claude Code plugin documentation](https://code.claude.com/docs/en/discover-plugins) for installation and updates.

## License

MIT. See [LICENSE](LICENSE).
