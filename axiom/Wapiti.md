



Wapiti is a free, open-source web application vulnerability scanner used to test the security of websites.

It works by crawling a website (like a browser) and then trying different attack techniques (such as SQL injection or XSS) to detect security weaknesses. It is a black-box tool, meaning it does not look at the source code—only the live website behavior.

## Installation

It is not supported by brew, but because it is Python-based you can install it easily via **pipx**:


**First**: Install pipx via Homebrew

```bash
brew install pipx
pipx ensurepath
```

This might ask you to restart the terminal.

**Second**: Install Wapiti using pipx
```bash
pipx install wapiti3
```
**Third**: Verify Installation
```bash
wapiti --version
```