# ss vs netstat – Markdown Cheat Sheet

## Kurzfassung

* **ss** = moderner Ersatz für **netstat**
* Schneller, detaillierter, besser filterbar
* Standard auf modernen Linux-Systemen

---

## Grundlegende Befehle

| Zweck             | netstat          | ss          |
| ----------------- | ---------------- | ----------- |
| Alle Verbindungen | `netstat -a`     | `ss -a`     |
| Listening Sockets | `netstat -l`     | `ss -l`     |
| TCP               | `netstat -t`     | `ss -t`     |
| UDP               | `netstat -u`     | `ss -u`     |
| Numerisch         | `netstat -n`     | `ss -n`     |
| Prozesse anzeigen | `netstat -p`     | `ss -p`     |
| Alles kombiniert  | `netstat -tulnp` | `ss -tulnp` |

---

## Häufige Use-Cases

### Welcher Prozess hört auf einem Port?

```bash
ss -tulnp | grep :80
```

### Alle aktiven TCP-Verbindungen

```bash
ss -t state established
```

### HTTPS-Verbindungen (Port 443)

```bash
ss state established '( dport = :443 or sport = :443 )'
```

### IPv4 / IPv6

```bash
ss -4 -tuln   # IPv4
ss -6 -tuln   # IPv6
```

---

## Performance & Debugging

### Verbindungsstatus zählen

```bash
ss -ant | awk '{print $1}' | sort | uniq -c
```

### Hohe Queues erkennen

```bash
ss -lnt
```

Achte auf hohe Werte in **Recv-Q** / **Send-Q**

---

## Ersatz für weitere netstat-Befehle

| netstat      | moderner Ersatz |
| ------------ | --------------- |
| `netstat -r` | `ip route`      |
| `netstat -i` | `ip -s link`    |
| `ifconfig`   | `ip addr`       |

---

## Merkhilfe

* `ss` = **Socket Statistics**
* Nutzt Netlink → schneller als `/proc`
* Ideal für Server, Container, Cloud

---

## Empfehlung

> **Neue Skripte immer mit `ss` schreiben**

---

