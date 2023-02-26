# Metadata Set Creator

Metadata Set Creator is an open source Python 3 project that has been created to create a Plex Meta Manager metadata file and associated set file for a list.

## Installing PMM Metadata Set Creator

Generally, PMM Metadata Set Creator can be installed in one of two ways:

1. Running on a system as a Python script [we will refer to this as a "local" install]
2. Running as a Docker container

GENERALLY SPEAKING, running as a Docker container is simpler, as you won't have to be concerned about installing Python, or support libraries, or any possible system conflicts generated by those actions.

For this reason, it's generally recommended that you install via Docker rather than directly on the host.

If you have some specific reason to avoid Docker, or you prefer running it as a Python script for some particular reason, then this general recommendation is not aimed at you.  It's aimed at someone who doesn't have an existing compelling reason to choose one over the other.

### Install Walkthroughs

There are no detailed walkthroguhs specifically for PMM Metadata Set Creator but the process is extremely similar to how you would do it with [Plex Meta Manager](https://metamanager.wiki/en/latest/home/installation.html#install-walkthroughs).

### Local Install Overview

PMM Metadata Set Creator is compatible with Python 3.11. Later versions may function but are untested.

These are high-level steps which assume the user has knowledge of python and pip, and the general ability to troubleshoot issues. 

1. Clone or [download and unzip](https://github.com/meisnate12/PMM-Metadata-Set-Creator/archive/refs/heads/master.zip) the repo.

```shell
git clone https://github.com/meisnate12/Metadata-Set-Creator
```
2. Install dependencies:

```shell
pip install -r requirements.txt
```

3. If the above command fails, run the following command:

```shell
pip install -r requirements.txt --ignore-installed
```

At this point PMM-Metadata-Set-Creator has been installed, and you can verify installation by running:

```shell
python metadata_set_creator.py
```

## Options

Each option can be applied in three ways:

1. Use the Shell Command when launching.
2. Setting the Environment Variable.
3. Adding the Environment Variables to `config/.env` 

| Option               | Description                                                                                                                                                                                                                                                          | Required |
|:---------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------:|
| List URL             | TMDb List, TMDb Collection, IMDb List, Trakt List, or MDbList List URL. <br>**Shell Command:** `-u` or `--url "https://trakt.tv/users/movistapp/lists/christmas-movies"` <br>**Environment Variable:** `URL=https://trakt.tv/users/movistapp/lists/christmas-movies` | &#9989;  |
| PMM Config           | Path to PMM Config with TMDb/Trakt configured. **Default:** `config/config.yml`<br>**Shell Command:** `-pm` or `--pmm-config "C:\Plex Meta Manager\config\config.yml"`<br>**Environment Variable:** `PMM_CONFIG=C:\Plex Meta Manager\config\config.yml`              | &#10060; |
| Timeout              | Timeout can be any number greater then 0. **Default:** `600`<br>**Shell Command:** `-ti` or `--timeout 1000`<br>**Environment Variable:** `TIMEOUT=1000`                                                                                                             | &#10060; |
| Season Placeholders  | Add Season posters placeholders.<br>**Shell Command:** `-s` or `--season`<br>**Environment Variable:** `SEASON=True`                                                                                                                                                 | &#10060; |
| Episode Placeholders | Add Episode posters placeholders.<br>**Shell Command:** `-e` or `--episode`<br>**Environment Variable:** `EPISODE=True`                                                                                                                                              | &#10060; |
| Trace Logs           | Run with extra trace logs.<br>**Shell Command:** `-tr` or `--trace`<br>**Environment Variable:** `TRACE=True`                                                                                                                                                        | &#10060; |
| Log Requests         | Run with every request logged.<br>**Shell Command:** `-lr` or `--log-requests`<br>**Environment Variable:** `LOG_REQUESTS=True`                                                                                                                                      | &#10060; |

### Example .env File
```
URL=https://trakt.tv/users/movistapp/lists/christmas-movies
PMM_CONFIG=C:\Plex Meta Manager\config\config.yml
TIMEOUT=600
SEASON=True
Episode=True
TRACE=False
LOG_REQUESTS=False
```