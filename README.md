# zurg

A self-hosted Real-Debrid webdav server written from scratch. Together with [rclone](https://rclone.org/) it can mount your Real-Debrid torrent library into your filesystem just like Dropbox.

## How to run zurg in 5 steps for Plex

1. Clone this repo `git clone https://github.com/debridmediamanager/zurg-testing.git`
2. Add your token in `config.yml`
3. `sudo mkdir -p /mnt/zurg`
4. Run `docker compose up -d`
5. `time ls -1R /mnt/zurg` You're done! If you do edits on your config.yml just do `docker compose restart zurg`.

A webdav server is also exposed to your localhost via port `9999`.

## Why zurg? Why not X?

- Better performance than anything out there; changes in your library appear instantly (assuming Plex picks it up fast enough)
- You should be able to access every file even if the torrent names are the same so if you have a lot of these, you might notice that zurg will have more files compared to others (e.g. 2 torrents named "Simpsons" but have different seasons, zurg merges all contents in that directory)
- You can configure a flexible directory structure in `config.yml`; you can select individual torrents that should appear on a directory by the ID you see in [DMM](https://debridmediamanager.com/).
- If you've ever experienced Plex scanner being stuck on a file and thereby freezing Plex completely, it should not happen anymore because zurg does a comprehensive check if a torrent is dead or not. You can run `ps aux --sort=-time | grep "Plex Media Scanner"` to check for stuck scanner processes.

## Please read our [wiki](https://github.com/debridmediamanager/zurg-testing/wiki) for more information!
