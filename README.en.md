# Debian 13 Server Reinstaller

A focused Debian 13 server reinstall tool derived from [bin456789/reinstall](https://github.com/bin456789/reinstall).

It supports standard and minimal Debian 13 installations on x86_64 and ARM64 systems with BIOS or UEFI boot.

> Warning: installation erases all data on the target disk. Back up the server first.

## Usage

```bash
curl -O https://raw.githubusercontent.com/zhangx16/dd-debian13-minimal/main/reinstall.sh
bash reinstall.sh
```

Debian 13 is selected automatically. The explicit form is also accepted:

```bash
bash reinstall.sh debian 13
```

For a reduced installation without the `standard` task or recommended packages:

```bash
bash reinstall.sh --minimal
```

OpenSSH and sudo are retained so that the installed server remains remotely manageable.

Examples:

```bash
bash reinstall.sh --minimal --password 'your-password'
bash reinstall.sh --minimal --ssh-key 'ssh-ed25519 AAAA...'
bash reinstall.sh --minimal --target-disk /dev/vda --ssh-port 2222
bash reinstall.sh --ci
```

Run `bash reinstall.sh --help` for the supported options.

## License

This project retains the upstream [GNU AGPLv3](LICENSE) license.
