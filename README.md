# YenScanner

Fast TCP port scanner written in C.



## Features

- **Fast** — multi-threaded (2000 threads by default)
- **Default scan** — top 1000 ports automatically
- **Custom ports** — single, range, list, or all 0-65535
- **Presets** — `web`, `common`, `top100`, `top1000`, `all`
- **Colored output** — service-based colors
- **Save results** — with `-o`
- **Single file** — no dependencies beyond POSIX
- **Service names** — recognizes 50+ known ports

## Install

```bash
git clone https://github.com/vnun0-yo/portscanner.git
```

```bash
cd portscanner
```

```bash
sudo apt install gcc 
```

```bash
sudo gcc -O3 -march=native -std=c11 -Wall -Wextra -Wno-unused-parameter -pthread -o YenScanner YenScanner.c
```

## Usage

```bash
YenScanner [OPTIONS] TARGET [TARGET...]
```

### Options

| Flag | Description |
|------|-------------|
| `-p, --ports SPEC` | Ports (default: top1000) |
| `-t, --threads N` | Threads (default: 2000) |
| `-T, --timeout MS` | Timeout in ms (default: 800) |
| `-o, --output FILE` | Save results to file |
| `--no-color` | Disable colors |
| `-q, --quiet` | Quiet mode |
| `-v, --verbose` | Print closed ports too |
| `-h, --help` | Show help |
| `--version` | Show version |

### Port formats

```
-p 80                  single port
-p 80,443,8080         list
-p 1-1000              range
-p all                 all 0-65535
-p -                   same as all
-p web                 web ports (80, 443, 8080, ...)
-p common              common CTF ports
-p top100              top 100 (nmap)
-p top1000             top 1000 (default)
```

### Examples

```bash
# top 1000 ports (default)
YenScanner 192.168.1.1

# all 0-65535
YenScanner 192.168.1.1 -p all

# specific ports
YenScanner 192.168.1.1 -p 22,80,443

# save to file
YenScanner 192.168.1.1 -o results.txt

# faster with more threads
YenScanner 192.168.1.1 -t 4000 -T 400

# multiple targets
YenScanner 192.168.1.1 192.168.1.2 example.com
```

## Sample Output

```
██╗   ██╗███████╗███╗   ██╗
╚██╗ ██╔╝██╔════╝████╗  ██║
 ╚████╔╝ █████╗  ██╔██╗ ██║
  ╚██╔╝  ██╔══╝  ██║╚██╗██║
   ██║   ███████╗██║ ╚████║
   ╚═╝   ╚══════╝╚═╝  ╚═══╝
  ──────────────────────────────────
  YenScanner  ·  fast port scanner

[*] Targets:   1
[*] Ports:     1000
[*] Threads:   2000
[*] Timeout:   800ms

[*] Scanning 192.168.1.1 (192.168.1.1)

[+] 22/tcp    open   ssh
[+] 80/tcp    open   http
[+] 443/tcp   open   https
[+] 3306/tcp  open   mysql
[+] 8080/tcp  open   http-proxy

[*] Target 192.168.1.1 done: 5 open ports

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  Summary
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  Targets     1
  Ports       1000 scanned
  Open        5
  Elapsed     2.34s
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

## Legal

For authorized testing only — systems you own, CTF challenges, lab environments, or bug bounty programs within scope.

Unauthorized port scanning is illegal in many jurisdictions.

# The Tool by - Yen
