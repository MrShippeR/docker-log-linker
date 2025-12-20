# Docker log linker

A minimalist terminal utility that create symbolic links to internal log files of Docker containers. Path to internal log files of docker can change, so it's good idea to create symlinks for this dynamic content. Destinaton of symlinks is fully configuratable via config in `/etc/docker-log-linker/docker-log-linker.conf`


---

## Features

- Creates **symbolic links** to internal logs of running Docker containers
- Configuratable user and group owner of symlinks
- CREATE_ALL_CONTAINERS_LOGS:
  - **false** - symlinks will be created only for containers defined in config file 
  - **true**  - symlinks for all started containers
- Symlink destinations:
  - **ONE_PLACE** – all container logs in one central directory
  - **SEPARATELY_DEFINED** – custom log directory per container
- Identification of Docker container by container_name or 12-character container_ID
- **Test mode** (`test`) – dry run, no system changes. To get output to terminal what symlinks will be created based on configuration file. `# docker-log-linker test`
- Syntax validation of configuration file
- Log file of utility in `/var/log/docker-log-linker/docker-log-linker.log`
- systemd service `systemctl status docker-log-linker.service`
- Distributed as a `.deb` package for easy instalation

---

## How it works

Docker stores container logs in internal paths under `/var/lib/docker/containers/`.

Basically, this utility process output of command `docker inspect --format='{{.LogPath}}' "$container_id"` to get dynamic destination and create symbolic link to this path in user defined path. It's core of this utility.
Process can be fully automated by enabling service `# systemctl enable docker-log-linker.service`. Utility is then started after Docker-ce package starts - with configuratable delay to get time for containers start/init.

---

## Installation and configuration

Download .deb package from github release folder and install it with package manager. For example:
`sudo dpkg -i docker-log-linker_1.0.deb` or
`sudo apt install docker-log-linker_1.0.deb`

Customize configuration file to match your situation:
`sudo nano /etc/docker-log-linker/docker-log-linker.conf`

Test your configuration with dry-run mode:
`sudo docker-log-linker test`

Start utility with:
`sudo systemctl start docker-log-linker.service`

See if utility works as desired:
`sudo systemctl status docker-log-linker.service`
`tail -f /var/log/docker-log-linker/docker-log-linker.log`

Enable auto-start of utility:
`sudo systemctl enable docker-log-linker.service`

---

## License

This project is licensed under the **GNU General Public License v3.0 (GPL-3.0)**.

---

## Disclaimer

This software is provided **as-is**, without any warranty.
Use it at your own risk.

---

## Contributions

Contributions are welcome!

If you:
- find a bug
- have a feature request
- want to suggest improvements
- want to submit a patch or enhancement

please open an **Issue** or **Pull Request** on GitHub.

---



