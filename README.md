# XAMPP for Windows CE

An unofficial mirror of the Apache Friends XAMPP distribution tailored for
Windows systems, including CE-compatible tooling. This repository contains the
pre-packaged binaries, configuration files, and helper scripts needed to run a
complete PHP development stack on Windows without manual installation.

## What's Included

This distribution bundles the following components:

- **Apache HTTP Server 2.4.58**
- **MariaDB 10.4.32** (drop-in replacement for MySQL)
- **PHP 8.2.12** (Thread Safe, VC16) with PEAR
- **phpMyAdmin 5.2.1**
- **OpenSSL 1.1.1p**
- **ADOdb 518a**
- **Mercury Mail Transport System v4.63** *(not shipped in the portable build)*
- **FileZilla FTP Server 0.9.41** *(not shipped in the portable build)*
- **Webalizer 2.23-04** *(not shipped in the portable build)*
- **Strawberry Perl 5.32.1.1 Portable**
- **Tomcat 8.5.96**
- **XAMPP Control Panel 3.3.0**
- **mailToDisk 1.0** (captures outbound mail to the local `mailoutput` folder)

Additional helper scripts for starting and stopping individual services (Apache,
MySQL, Mercury, FileZilla, Tomcat) are located in the repository root.

## System Requirements

- 64 MB RAM or more (recommended)
- 750 MB of free disk space
- Windows 7, 8, or 10
- Microsoft Visual C++ 2019 Redistributable (VC++ 16). Download from the
  [Microsoft website](https://www.microsoft.com/en-us/download/) and install it
  before running PHP 8.2 binaries.

## Installation

1. **Download or clone the repository** to the Windows machine on which you
   plan to run XAMPP.
2. **Extract** the archive or copy the folder to the root of a drive (for
   example `C:\xampp`). For portable deployments on removable media (USB, SD),
   ensure the directory is at the top level of the volume (for example
   `E:\xampp`).
3. **Do not run** `setup_xampp.bat` when using a portable/USB installation. The
   package is pre-configured for relative paths in that scenario.
4. **Launch** `xampp-control.exe` to open the control panel and manage services.

> **Tip:** If you downloaded the repository as a ZIP file from GitHub, right
> click the archive, choose *Extract All...*, and select the desired drive root.

## Usage

### Starting Services

- Open `xampp-control.exe` and click **Start** next to Apache, MySQL, FileZilla,
  Mercury, or Tomcat as needed.
- Alternatively, run the provided batch files (for example,
  `apache_start.bat`, `mysql_start.bat`, `filezilla_start.bat`, `mercury_start.bat`).

### Stopping Services

- Use the **Stop** buttons in `xampp-control.exe`, or run the matching `*_stop.bat`
  scripts.

### Accessing the Dashboard

- After starting Apache, visit `http://localhost/` in your browser to confirm
  the stack is running.
- The bundled phpMyAdmin instance is available at `http://localhost/phpmyadmin/`
  for database management.

### Mail Testing

- All outbound mail sent through PHP is redirected to the local
  `mailoutput` folder (configured via mailToDisk). Open the `.eml` files in a
  mail client to inspect test messages.

## Directory Layout

- `apache/`, `mysql/`, `php/`, `perl/`, `tomcat/`: Core server and language
  runtimes.
- `htdocs/`: Default web root. Place your PHP applications here.
- `phpMyAdmin/`: Web-based database administration tool.
- `MercuryMail/`, `FileZillaFTP/`: Supporting service binaries.
- `tmp/`, `logs/` (inside service directories): Runtime files and logs.
- `setup_xampp.bat`, `xampp_start.exe`, `xampp_stop.exe`: Helper scripts for
  configuration and service orchestration.

## Configuration Tips

- Edit `apache\conf\httpd.conf` to change Apache ports, document root, or enable
  additional modules.
- Update `php\php.ini` to tweak PHP settings such as `extension_dir`, `memory_limit`,
  and `error_reporting`.
- Modify `mysql\bin\my.ini` to adjust database settings (ports, buffer sizes).
- Tomcat settings live in `tomcat\conf\server.xml` and related files.

Whenever you modify configuration files, restart the affected service to apply
changes.

## Troubleshooting

- If Apache or MySQL fail to start, check the service log files:
  - `apache\logs\error.log`
  - `mysql\data\*.err`
- Ensure no other application is listening on the default ports (80 for Apache,
  443 for HTTPS, 3306 for MariaDB).
- Confirm that the VC++ 2019 Redistributable is installed when PHP exits with
  missing DLL errors.
- Run the control panel as an administrator when starting services on Windows
  with UAC enabled.

## Additional Resources

- XAMPP documentation: <https://www.apachefriends.org/index.html>
- Community forums: <https://community.apachefriends.org/>
- MariaDB documentation: <https://mariadb.com/kb/en/>
- PHP documentation: <https://www.php.net/docs.php>

This repository provides the binaries and scripts as-is. Refer to the links
above for in-depth configuration guidance and best practices.
