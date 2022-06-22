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

## Server

The server can only be accessed from Codam iMacs or from the the "Codam -
Student" wifi network. The IP address is `10.16.1.1`.

The website code is cloned at `/srv/website` and is owned by the `hivemind`
user. One shouldn't have to touch this directly directly, and should instead
use the `website-deploy` command to update the website (see "How to publish").

The `website-deploy` script is located at `/usr/local/bin/website-deploy` and
simply pulls the git to get the latest version and builds it using `hugo`. The
output is stored at `/var/www/html` where it is hosted by `nginx` (see
`/etc/nginx/sites-enabled/default`).

TLS (https) is not handled by our server, we are expected to simply host at
port 80 and the reverse proxy managed by Codam will all TLS.

### Adding a new user to the server

1. Login as an existing user
2. Create a new user (replacing `USERNAME` with the desired username):
   ```sh
   sudo adduser USERNAME
   ```
   The tool will ask for a few questions like Full Name and Room Number, you
   can leave all those empty.
3. Add the new user to the `sudo` group so that they are able to run commands
   as root:
   ```sh
   sudo adduser USERNAME sudo
   ```
4. Login as the new user:
   ```sh
   sudo su USERNAME
   ```
5. Add the new user's SSH keys:
   ```sh
   mkdir ~/.ssh
   vim ~/.ssh/auhtorized_keys # Use whatever commands you want to popualte the `authorized_keys` file.
   chmod 600 ~/.ssh/authorized_keys
   ```
