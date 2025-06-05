# xapply

`xapply` is a command line tool for saving and restoring XFCE appearance profiles. It captures the desktop background settings for all monitors and workspaces along with the Gtk+ and icon themes. Profiles are saved under `~/.config/xapply` and can be applied later on.

## Usage

```bash
xapply save <profile-name>    # Save current appearance profile
xapply apply <profile-name>   # Apply an existing appearance profile
```

## Design overview

The utility relies on `xfconf-query` to read and write XFCE configuration values. Saving a profile collects relevant keys from the `xsettings` and `xfce4-desktop` channels and stores them in a JSON file. Applying a profile replays the stored keys using `xfconf-query` so the appearance is restored in one step.

