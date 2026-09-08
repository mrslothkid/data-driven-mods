# Data-Driven Mods

Changes pushed to `main` are deployed automatically by [GitHub Actions](.github/workflows/deploy_files_tailscale.yml). The workflow connects to the server over Tailscale and SSH, in order to upload the files.

## Repository Structure

| Path | Purpose |
| --- | --- |
| `mods/` | Minecraft mod `.jar` files. |
| `datapacks/` | Datapack folders or `.zip` files. |
| `resourcepack/assets/` | Minecraft assets and namespaced custom assets. |
| `resourcepack/pack.mcmeta` | Resource-pack metadata. |
| `resourcepack/resourcepack.zip` | Generated resource-pack archive. |
| `resourcepack/resourcepack.sha` | Generated SHA-1 checksum for the archive. |

## Adding Mods and Datapacks

1. Add mod `.jar` files directly to `mods/`.
2. Add datapack folders or `.zip` files to `datapacks/`.
3. Commit and push the changes to `main`, or open a pull request for review.
4. After the change reaches `main`, the workflow syncs the files to the server.

## Adding Resource-Pack Assets

1. Add vanilla overrides under `resourcepack/assets/minecraft/`.
2. Add custom content under `resourcepack/assets/<namespace>/`.
3. Update `resourcepack/pack.mcmeta` when the pack metadata needs to change.
4. Commit and push the changes to `main`.

The workflow creates `resourcepack/resourcepack.zip`, calculates its SHA-1, writes the value to `resourcepack/resourcepack.sha`, and updates the server's `resource-pack-sha1` setting.

## Notes

Please ask before removing or editing any mods or datapacks or resource pack stuff. 
Changes may not take effect until the server is restarted, which is currently manual/performed on request.

