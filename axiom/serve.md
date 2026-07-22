Here is a concise reference document in Markdown covering `serve`.

Markdown

````
# serve (1) — Static File Serving Utility

## Overview
`serve` is a lightweight, single-command Node.js utility designed to serve static websites, single-page applications (SPAs), and directory listings over HTTP.

---

## Installation

### Global Installation
Install globally using `npm`:

```bash
npm install -g serve
````

### On-Demand Execution

Execute directly without permanent installation via `npx`:

Bash

```
npx serve [target_directory]
```

## Technical Capabilities & Configuration

### Primary Features

- **Static File Delivery:** Serves HTML, CSS, JavaScript, media assets, and arbitrary static resources.
    
- **SPA Routing Support:** Automatically redirects unmatched path requests to `index.html` via the single-page application flag (`-s` or `--single`).
    
- **CORS Management:** Enables Cross-Origin Resource Sharing headers by default.
    
- **Directory Browsing:** Generates interactive directory index listings when no `index.html` is present.
    
- **HTTP/2 Support:** Provides TLS/SSL support using custom cert/key pairs.
    

### Common CLI Options

|**Flag**|**Parameter**|**Description**|
|---|---|---|
|`-l`, `--listen`|`[host:]port` \| `path`|Binds server to specific host, port, or UNIX socket.|
|`-s`, `--single`|N/A|Enables SPA fallback mode (rewrites all 404 routes to `/index.html`).|
|`-d`, `--debug`|N/A|Output detailed request logs and internal state.|
|`-c`, `--config`|`path`|Path to custom configuration file (`serve.json`).|
|`--cors`|N/A|Explicitly inject `Access-Control-Allow-Origin: *` response headers.|
|`--ssl-cert`|`path`|Path to SSL certificate for HTTPS/HTTP2 listener.|
|`--ssl-key`|`path`|Path to SSL private key.|

## Execution Examples

### Basic Static Directory Hosting

Serve the current working directory on default port `3000`:

Bash

```
serve
```

### Custom Directory and Port Binding

Serve target directory `/var/www/dist` on port `3333`:

Bash

```
serve /var/www/dist -l 3333
```

### Bind Exclusively to Loopback Interface

Restrict external network access by binding strictly to `localhost`:

Bash

```
serve /var/www/dist -l tcp://127.0.0.1:3333
```

### Single-Page Application (SPA) Mode

Route all client-side navigation paths back to the root `index.html`:

Bash

```
serve -s /var/www/app -l 8080
```

## Configuration File (`serve.json`)

Advanced server runtime behaviors (rewrites, redirects, header manipulation, and clean URLs) can be defined using a `serve.json` file inside the target root directory:

JSON

```
{
  "public": "dist",
  "cleanUrls": true,
  "rewrites": [
    { "source": "app/**", "destination": "/index.html" }
  ],
  "headers": [
    {
      "source": "**/*.@(js|css)",
      "headers": [{
        "key": "Cache-Control",
        "value": "max-age=31536000"
      }]
    }
  ]
}
```