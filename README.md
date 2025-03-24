🔍 PTRex 🦖 Reverse DNS Lookup Script
This Bash script performs reverse DNS (PTR) lookups on a given IP, CIDR range, or a list of IPs from a file. It efficiently resolves hostnames using `getent hosts`, tracks progress, and runs queries in parallel for speed.

🚀 Features
✅ Accepts a single IP, CIDR range, or file with multiple IPs
✅ Uses `getent hosts` for reverse DNS (PTR) lookups 🔄
✅ Parallel execution (up to 50 requests at a time) for faster results ⚡
✅ Tracks progress dynamically 📊
✅ Filters and outputs only successful PTR lookups (hostnames only) 🛠

🚀 Installation
Ensure you have `prips` installed for CIDR expansion:

```
bash
sudo apt install prips
```

🚀 Usage
Run the script and enter an IP, CIDR range, or a file path when prompted:

```
bash
./PTRex
```

*📌 Example Inputs*
1️⃣ Single IP: `8.8.8.8`
2️⃣ CIDR Range: `192.168.1.0/24`
3️⃣ File with IPs: `/path/to/ips.txt`

*📜 Output Example*
```
[+] Processing IPs from file: ips.txt
[+] Requests made: 12 / 100
[+] Completed!
✅ -> example.com
✅ -> mail.google.com
✅ -> somehost.net
```

🔎 How It Works
1️⃣ User Input

- Prompts user to enter an IP, CIDR, or file path
- Determines input type (single IP, CIDR, or file)

2️⃣ IP Expansion (if CIDR)

- Uses `prips` to generate a list of IPs from the CIDR range

3️⃣ Parallel Reverse DNS Lookups

- Uses `getent hosts` to fetch PTR records 🕵️
- Runs up to 50 parallel lookups using `xargs -P 50`
- Displays live progress updates

4️⃣ Output Processing

- Saves only successful hostname lookups 🎯
- Hides IPs, displaying hostnames only

5️⃣ Cleanup

- Deletes temporary files after execution 🧹

⚠️ Notes
⚡ Only successful lookups (resolved hostnames) are displayed
⚡ Parallel execution speeds up large queries
⚡ If `prips` is missing, CIDR expansion will fail

🔮 Future Improvements
✨ Add logging for debugging
✨ Implement timeouts for slow DNS responses
✨ Support custom concurrency levels

This script is great for security assessments, network mapping, and passive reconnaissance when identifying hostnames associated with an IP range. 🌍
