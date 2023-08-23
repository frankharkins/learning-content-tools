# IBM Quantum Learning content tools

Scripts and actions to help maintainers of IBM Quantum Learning content.


## Syncing with the content database

To sync your lessons automatically with the database, you'll need to
add a `iql.conf.yaml` to the root of your content folder.

```yaml
# iql.conf.yaml
# This goes in the root of your content folder
lessons:
 - path: path/to/folder  # path to folder containing the lesson
   # lesson IDs in the databases:
   idStaging: 4e85c04a-c2fb-4bfc-9077-b75bf1b73a25
   idProduction: 5026731b-5e7b-4585-8cf2-f24482819e21
```

To upload lessons using our script:

1. Install the package
   ```bash
   pip install git+https://github.com/frankharkins/learning-content-tools.git#subdirectory=iql-lesson-sync
   ```
2. Run this from the root of your content folder:

   ```bash
   sync-lessons
   ```
   You'll be prompted for your username and password.

You can also upload just one lesson at a time using

```bash
sync-lessons path/to/folder
```

To use this script as part of CI (Travis / GitHub actions), set the
`LEARNING_API_TOKEN` environment variable to your access token before running
the script, and `LEARNING_API_ENVIRONMENT` to the name of the database (`staging` or
`production`).
