# dark-visitors-robots
GitHub action to automatically update robots.txt from darkvisitors.com.

To use it:
1. Create a project at darkvisitors.com and get an access token: https://darkvisitors.com/docs/robots-txt
2. Add a secret named `DARK_VISITORS_ACCESS_TOKEN` to your repository whose value is the access token
3. Create a GitHub action with a single step. Here's an example that runs daily and can also be triggered manually. Fill in `$MINUTE` and `$HOUR` to designate when your `robots.txt` should be updated each day.
```
name: Fetch and Commit robots.txt
# https://darkvisitors.com/docs/robots-txt

on:
  schedule:
    - cron: "$MINUTE $HOUR * * *"
  workflow_dispatch:  # Allow manual triggers

jobs:
  fetch-and-commit:
    runs-on: ubuntu-latest

    steps:
    - name: Dark Visitors robots.txt
      uses: valrus/dark-visitors-robots@v1.2.0
      with:
        access-token: ${{ secrets.DARK_VISITORS_ACCESS_TOKEN }}
    - name: Dark Visitors robots.txt
      uses: valrus/dark-visitors-robots@v1.2.0
      with:
        access-token: ${{ secrets.DARK_VISITORS_ACCESS_TOKEN }}
```
