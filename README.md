# Cloudflare DDNS Updater

This is a simple Bash script to update a Cloudflare DNS record with your current public IP address, allowing you to use your domain like a dynamic DNS (DDNS) service. Great for self-hosted setups with dynamic IPs!

## Summary

- Updates your A or AAAA DNS record using Cloudflare's API.
- Works with dynamic IP addresses.
- Easy to run manually or automate with cron.
- Keeps your API keys secure with a `.env` file.

## 🛠️ Setup

### 1. Clone this repo

```bash
git clone https://github.com/ricky-yosh/cloudflare-ddns-script.git
cd cloudflare-ddns-script
```

### 2. Create your `.env` file

Create a `.env` file based on the provided `.env.example`:

```bash
cp .env.example .env
```

Then fill in your details:

```ini
CF_API_TOKEN=your_cloudflare_api_token
ZONE_ID=your_zone_id
RECORD_NAME=home.example.com
RECORD_TYPE=A
```

> 🔐 **Important:** Never commit your `.env` file. It’s in `.gitignore`.

### 3. Run the script

Make the script executable and run it:

```bash
chmod +x update.sh
./update.sh
```

---

## ⏰ Automate with Cron

Run the script every 10 minutes:

```bash
crontab -e
```

Add the line:

```bash
*/10 * * * * /path/to/your/cloudflare-ddns/update.sh >/dev/null 2>&1
```

---

## 📁 File Structure

```
cloudflare-ddns-script/
├── update.sh         # Main script
├── .env              # Your secret config (not tracked by git)
├── .env.example      # Template for your .env
├── .gitignore        # Prevents .env from being committed
└── README.md         # This file
```

---

## Notes

* Requires `curl` and `jq` install with:
```sh
sudo apt install curl jq`
```
* API token must have permissions: `Zone:DNS:Edit` and `Zone:Zone:Read`.

---

## 🔐 Security

**Do not publish your `.env` or hardcode sensitive tokens into your scripts.**
---
