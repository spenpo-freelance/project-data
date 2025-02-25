# project-data
## a template for project data

This template is an example implementation of [Spencer Pope](https://github.com/spope851)'s backup-sync ([wp-env-backup-sync](https://github.com/marketplace/actions/wordpress-environment-backup-sync)) composite action

See [workflow documentation](https://github.com/spope851/wp-env-backup-sync) for more information

## Setup

1. Create a new repository from this template
2. Add all required secrets from the documentation to your repository or organization
3. Update the `PROJECT_PATH`, `PROJECT_DOMAIN`, and `PROJECT_ENCRYPTION_PASSWORD` secrets in the new repository
4. Delete this readme, the changie files (.changie.yaml, .changes/, CHANGELOG.md), and add your own readme explaining the project you're using backup-sync for and how backup-sync is used to support the project

## Usage

- Add a directory in the /backup and /migration directories for each environment you want to support
- Add source_env and target_env input options to the workflow (./github/workflows/backup-sync.yml) for each environment
- Add/remove other inputs as needed
- Edit the default values for skip_tables and sync_content_dirs in the with section of the Backup Sync step as needed. You can always add additional skip_tables or sync_content_dirs on the fly when kicking off the workflow from the GitHub UI, but you cannot ignore your defaults there
- If you want to be able to ignore any of your defaults, you can do setup an input like the `migrate_users` example in the template to conditionally remove values from your chosen defaults on the fly

## Notes

- The template does not migrate wp_comments, wp_commentmeta, wp_lightspeed_url, wp_lightspeed_url_file, wp_users, or wp_usermeta by default. Edit those if your are not using lightspeed or want to include/exclude other tables from your workflow
- The template migrates uploads, themes, and plugins by default. You can add languages, mu-plugins, and other content directories to the sync_content_dirs input if needed
