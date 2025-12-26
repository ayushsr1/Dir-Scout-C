# DirScout (C)

A lightweight, command-line directory enumeration tool written in **C** for basic web reconnaissance.
DirScout performs fast directory brute-forcing using **HTTP HEAD requests** to identify potentially valid or restricted paths on a web server.

---

## 🎯 Purpose

The goal of this project is to demonstrate:

* understanding of basic web reconnaissance techniques
* knowledge of HTTP request methods and response codes
* efficient network requests using **libcurl**
* low-level implementation of security tools in **C**
* building minimal, dependency-light CLI utilities

This tool is intended for **learning, controlled testing, and authorized security assessments only**.

---

## 🔧 Features

* Fast directory enumeration using a wordlist
* Uses **HTTP HEAD** requests for efficiency (no response body download)
* Detects commonly interesting HTTP response codes:

  * `200` (OK)
  * `301` / `302` (Redirects)
  * `403` (Forbidden)
* Minimal external dependencies (**libcurl only**)
* Simple and readable output suitable for manual analysis

---

## 🧩 How It Works (High Level)

1. The user provides:

   * a base URL
   * a wordlist file containing directory names
2. DirScout reads each entry from the wordlist
3. For each entry:

   * it constructs a full URL (`base_url/word`)
   * sends an **HTTP HEAD request**
4. The server’s HTTP status code is checked
5. If the response code indicates a potentially valid or protected path, it is printed

No content is downloaded, making the process lightweight and fast.

---

## 🚀 Usage

### Prerequisites

* GCC or compatible C compiler
* `libcurl` development library installed

On Debian/Ubuntu:

```bash
sudo apt install libcurl4-openssl-dev
```

---

### Build

```bash
make
```

---

### Run

```bash
./dirscout https://example.com wordlists/common.txt
```

---

## 📌 Notes

* This tool performs **basic enumeration only**
* It does not attempt authentication bypass, fuzzing, or exploitation
* Results should be manually reviewed — a valid status code does not always mean a real directory
* Designed for simplicity and learning, not large-scale scanning

---

## ⚠️ Legal & Ethical Notice

DirScout is intended for **educational purposes and authorized security testing only**.

* Do not use this tool against systems you do not own or have explicit permission to test
* Unauthorized scanning may be illegal or unethical depending on jurisdiction

---

## 🧠 Design Philosophy

* Keep the tool minimal and understandable
* Avoid unnecessary abstractions
* Prefer clarity over feature overload
* Focus on fundamentals of web reconnaissance

---
