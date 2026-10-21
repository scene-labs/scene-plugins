# Scene Labs plugins

Skills for Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, and OpenCode for authoring animated Scene diagrams: Mermaid and PlantUML sequence diagrams, Mermaid flowcharts, and Mermaid state diagrams.

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

## Cursor

For a personal or project skill, use GitHub CLI 2.90 or later. Run this in your project repository:

```sh
gh skill install scene-labs/scene-plugins scene --agent cursor --scope project
```

Restart your agent session and ask for a Scene diagram. To update the installed skill, run `gh skill update scene --dir .agents/skills` from the same project. This is a manual update path.

### Cursor team marketplace

Teams and Enterprise admins can import `https://github.com/scene-labs/scene-plugins` under **Dashboard → Plugins & MCPs → Team Marketplaces → Add Marketplace → Import from Repo**. Add Scene to the marketplace, then install it from **Customize**.

For automatic refresh, enable **Marketplace Settings → Enable Auto Refresh** and connect the Cursor GitHub App to the repository. Admins can also use **Refresh** manually. This requires the relevant repository access; importing this public repository does not grant that access. The repository includes a Cursor marketplace manifest; it is not yet listed in Cursor's reviewed public marketplace.

## GitHub Copilot

With GitHub CLI 2.90 or later, run this in your project repository:

```sh
gh skill install scene-labs/scene-plugins scene --agent github-copilot --scope project
```

Restart your agent session. The installed skill is available to Copilot's supported agents; commit the project skill if your team or cloud agent needs it. To update it, run `gh skill update scene --dir .agents/skills` from the same project. Updates are manual.

## Gemini CLI

Run in your terminal:

```sh
gemini extensions install https://github.com/scene-labs/scene-plugins --auto-update
```

Review and accept the extension installation prompt, then restart Gemini CLI. The extension loads the shared Scene authoring reference as context whenever enabled. It has no MCP servers or executable hooks.

The install flag enables automatic updates. For a manual update, run:

```sh
gemini extensions update scene
```

## OpenCode

With GitHub CLI 2.90 or later, run this in your project repository:

```sh
gh skill install scene-labs/scene-plugins scene --agent opencode --scope project
```

Restart OpenCode and ask for a Scene diagram. OpenCode discovers the installed project skill directly; no JavaScript plugin is needed. To update it, run `gh skill update scene --dir .agents/skills` from the same project. Updates are manual.

## Inspect before installing

Use `gh skill preview scene-labs/scene-plugins scene` to inspect the shared reference. Avoid installing another copy if your agent already loads Scene.

## Use

Ask your agent to create a Scene diagram or add Scene annotations to an existing diagram. In Claude Code, you can also invoke the skill explicitly:

```text
/scene:scene Describe your system interaction here
```

The skill teaches your agent Scene's annotations and playback behavior. It does not install or run the Scene viewer.

If you previously copied a standalone Scene skill into your Claude skills directory, remove that old copy after confirming the plugin works so you do not keep loading outdated instructions.

## Publish an update

1. Update `plugins/scene/skills/scene/SKILL.md` from the current Scene authoring reference.
2. Bump `version` together in `plugins/scene/plugin.json`, `plugins/scene/.claude-plugin/plugin.json`, `plugins/scene/.cursor-plugin/plugin.json`, and `gemini-extension.json`. Do not put a second version in either marketplace catalog. Claude users do not receive changed files without a version bump.
3. Validate both the plugin and marketplace:

   ```sh
   claude plugin validate ./plugins/scene
   claude plugin validate .
   ```

4. Check Codex discovery with `codex plugin list --marketplace scene-labs --available --json` from this repository.
5. Test GitHub CLI skill installation, Gemini extension packaging, and each available client before pushing to `main`. Review changes before publishing.

Keep the published skill synchronized with the Scene docs and onboarding instructions when the syntax changes.

Use Scene Labs as both the git author and committer, with a non-personal email address. Do not copy personal repository history or include personal account links in published files.

See the [Claude Code plugin documentation](https://code.claude.com/docs/en/discover-plugins) for installation and updates.

## License

MIT. See [LICENSE](LICENSE).
