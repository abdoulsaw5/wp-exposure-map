# WP Exposure Map
Link: https://abdoulsaw5.github.io/wp-exposure-map/
A static reference tool that catalogs known-sensitive WordPress endpoints (configuration files, backup artifacts, REST API routes, admin surfaces, and more) organized by risk level. Paste in a domain and it generates clickable reference links across dozens of categories, each with a note explaining *why* that endpoint matters.

Built as a checklist for authorized security research and penetration testing, not an automated scanner. It doesn't send any requests on your behalf: it only builds URLs. All verification is done manually by the researcher.

---

## ⚠️ Authorized Use Only

This tool is intended strictly for:

- Security research on **assets you own**
- Engagements where you have **explicit written authorization** (e.g. a signed pentest agreement or a bug bounty program's defined scope)
- Educational / learning purposes (e.g. setting up a local WordPress instance to test against)

Unauthorized access to computer systems is illegal in most jurisdictions (e.g. the U.S. Computer Fraud and Abuse Act, UK Computer Misuse Act, and equivalent laws elsewhere). The author assumes no responsibility for misuse of this tool. If you don't have permission to test a domain, don't point this at it.

---

## What it does

- You enter a domain.
- The tool generates a list of well-known WordPress paths as clickable links (`https://yourdomain.com/wp-config.php`, etc.), grouped into categories like credential exposure, backup files, REST API user enumeration, vulnerable plugin surfaces, and more.
- Each endpoint has a **risk tag** (Critical / High / Medium / Low) and a short note on why it's relevant.
- Filter by risk level to prioritize what to check first.

## What it does *not* do

- It does **not** send any HTTP requests automatically: no status-code checking, no scanning.
- It does **not** exploit anything. It's a link/checklist generator, not an attack tool.
- It does **not** guarantee an endpoint exists or is exploitable on any given target. Presence of a link here just means "worth checking," not "vulnerable."

## Methodology / Sourcing

The endpoint list is compiled from:

- WordPress core's publicly documented file/directory structure
- Publicly disclosed CVEs and plugin changelogs (e.g. Slider Revolution, TimThumb, WP File Manager)
- Common misconfiguration patterns documented by the security research community (backup naming conventions, forgotten dev tools, cache drop-ins, etc.)
- Patterns referenced in open-source recon tooling and wordlists (e.g. WPScan's database, common `ffuf`/`gobuster` wordlists)

This is **not** a leaked or proprietary list. Everything here is derived from publicly available security research. Endpoint *presence* should always be followed by manual version-checking against a CVE database before treating anything as a confirmed finding.

## Usage

1. Open `wp-endpoints.html` in a browser (or visit the hosted GitHub Pages link, if enabled).
2. Enter a domain you're authorized to test.
3. Click through the generated links, or filter by risk level to focus your review.

No install, no dependencies. It's a single self-contained HTML file.

## Contributing

Found an endpoint that should be added, or a note that needs correcting? PRs and issues are welcome. Please include a source (CVE, changelog, disclosure writeup) for any new entries so the list stays grounded in verifiable research rather than guesswork.

## License

MIT. See [LICENSE](LICENSE).

## Disclaimer

This project is provided for educational and authorized security research purposes only. The author is not responsible for any misuse or damage caused by this tool.
