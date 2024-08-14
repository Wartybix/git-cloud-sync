# Enable 'cloud' functionality in locally installed games

If you use Steam, Epic/Heroic, Rockstar, etc. launchers, then cloud-syncing 
should already be inbuilt.
However, locally installed games, such as those downloaded from itch.io, don't
have this functionality out-of-the-box.
Instead, we can try to implement cloud saving through Git.

## How to use
### Make modifications to this repo
Clone this repository into where your game save is located.

`git clone https://github.com/Wartybix/git-cloud-sync`

Change the remote origin URL to point to your own forked repository:

`git remote set-url origin https://github.com/your-username/your-game-cloud-save`

Alternatively you can fork this repository in GitHub first, and just clone your
forked repository, in which case you shouldn't need to change the origin URL
afterwards.

Change the `upload-script.sh` script to include the save file(s) of your game
where the commented line is.

### Run the upload/download scripts automatically when running the game

#### Lutris Method

In your game's advanced options in Lutris, enter the path of `download-script.sh`
into the _Pre-launch script_ field. Set _Wait for pre-launch script completion_
to **on**. Enter the path of `upload-script.sh` into the _Post-exit script_ field.

Incoming changes should be pulled from the remote repository just before the 
game is opened, and local changes should be pushed immediately after closing
the game.

#### Wrapper Method

If you are not using Lutris to open your locally-installed games, you can
instead change your game's `.desktop` file to point to `game-wrapper.sh` for its
`exec` field. Open `game-wrapper.sh` and add the path of the game's executable
where the commented line is.
