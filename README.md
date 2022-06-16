# Codam Student Council Website

## Dependencies

Install [hugo](https://repology.org/project/hugo-sitegen/versions) using your
package manager.

## Submodule

This repo uses submodules. To clone them, run `git submodule update --init`.

## Testing

To test locally, run `hugo server`.

## How to publish

1. Push the code to the origin at `git@github.com:CodamStudentCouncil/website.git`.
2. SSH to the server
3. Run the `website-deploy` command as the `hivemind` user:
   ```sh
   sudo -u hivemind website-deploy
   ```
