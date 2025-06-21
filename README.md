# EasyIp - Comprehensive Bash IP Information Lookup Tool

## Features

- 🌐 **IP Geolocation**: Country, region, city, postal code, timezone
- 🗺️ **Coordinates**: Latitude/longitude with map integration
- 🏢 **Network Info**: ASN, organization, hostname
- 🔒 **Privacy Detection**: VPN, proxy, Tor exit node detection
- 📱 **Carrier Info**: Mobile carrier information
- 🚨 **Abuse Contact**: Contact information for abuse reports
- 💾 **Caching**: Local caching for improved performance
- 📊 **Multiple Formats**: Human-readable, JSON, compact, and table output
- 🗺️ **Map Integration**: Open location in browser maps
- ⚙️ **Configurable**: Customizable settings via config file

## Installation

1. **Download the script**:
   ```bash
   wget https://raw.githubusercontent.com/poaxy/EasyIP/refs/heads/main/easyip
   ```

2. **Make it executable**:
   ```bash
   chmod +x easyip
   ```

3. **Move to your PATH** (optional):
   ```bash
   sudo mv easyip /usr/local/bin/
   ```

4. **Install dependencies**:
   ```bash
   # Ubuntu/Debian
   sudo apt install curl jq

   # CentOS/RHEL
   sudo yum install curl jq

   # Fedora
   sudo dnf install curl jq

   # macOS
   brew install curl jq
   ```

## Configuration

### API Key Setup

1. Get a free API key from [IPinfo](https://ipinfo.io/account)
2. Create configuration:
   ```bash
   easyip --config
   ```
3. Add your API key to the config file:
   ```bash
   API_KEY=your_ipinfo_api_key_here
   ```

### Configuration File

Location: `~/.config/easyip/config`

```bash
# easyip Configuration File
API_KEY=your_ipinfo_api_key_here
DEFAULT_FORMAT=human
CACHE_ENABLED=true
CACHE_DURATION=3600
TIMEOUT=10
DEFAULT_BROWSER=firefox
```

## Usage

### Basic Usage

```bash
# Lookup current public IP
easyip

# Lookup specific IP
easyip 1.1.1.1

# JSON output
easyip 1.1.1.1 -j

# Compact output
easyip 1.1.1.1 -c

# Table output
easyip 1.1.1.1 -t
```

### Advanced Options

```bash
# Open location in map
easyip 1.1.1.1 --map

# Use custom API key
easyip 1.1.1.1 -k your_api_key

# Set timeout
easyip 1.1.1.1 --timeout 15

# Disable caching
easyip 1.1.1.1 --no-cache

# Clear cache
easyip --clear-cache

# Edit configuration
easyip --config

# Verbose output
easyip 1.1.1.1 --verbose
```

### Output Examples

#### Human-readable Format
```
🌐 IP Information for 1.1.1.1
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📍 Location:
   Sydney, New South Wales, AU
   📮 Postal: 2000
   🕐 Timezone: Australia/Sydney

🏢 Network:
   🌐 Hostname: one.one.one.one
   🏢 Organization: AS13335 Cloudflare, Inc.

🗺️  Coordinates:
   📍 -33.8688,151.2093
   🗺️  Map: https://maps.google.com/?q=-33.8688,151.2093
```

#### JSON Format
```json
{
  "ip": "1.1.1.1",
  "hostname": "one.one.one.one",
  "city": "Sydney",
  "region": "New South Wales",
  "country": "AU",
  "loc": "-33.8688,151.2093",
  "org": "AS13335 Cloudflare, Inc.",
  "postal": "2000",
  "timezone": "Australia/Sydney"
}
```

#### Compact Format
```
1.1.1.1 | Sydney, New South Wales, AU | AS13335 Cloudflare, Inc. | -33.8688,151.2093
```

## Command Line Options

| Option | Description |
|--------|-------------|
| `-h, --help` | Show help message |
| `-v, --version` | Show version information |
| `-j, --json` | Output in JSON format |
| `-c, --compact` | Output in compact format |
| `-t, --table` | Output in table format |
| `-k, --api-key KEY` | Use custom API key |
| `--timeout SECONDS` | Set request timeout |
| `--no-cache` | Disable caching |
| `--clear-cache` | Clear cache directory |
| `--config` | Edit configuration file |
| `--map` | Open location in browser map |
| `--verbose` | Enable verbose output |

## API Information

This script uses the [IPinfo API](https://ipinfo.io/) which provides:

- **Free Tier**: 50,000 requests/month
- **Rate Limits**: Varies by plan
- **Data Sources**: Multiple geolocation databases
- **Privacy**: GDPR compliant

### API Response Fields

| Field | Description |
|-------|-------------|
| `ip` | IP address |
| `hostname` | Reverse DNS hostname |
| `city` | City name |
| `region` | Region/state |
| `country` | Country code |
| `loc` | Latitude,longitude |
| `org` | ASN and organization |
| `postal` | Postal code |
| `timezone` | Timezone |
| `privacy` | Privacy detection info |
| `abuse` | Abuse contact info |

## Caching

The script caches API responses locally to:
- Reduce API calls
- Improve response time
- Respect rate limits

- **Cache Location**: `~/.config/easyip/cache/`
- **Cache Duration**: 1 hour (configurable)
- **Cache Format**: JSON files named by IP

## Error Handling

The script handles various error conditions:
- Invalid IP addresses
- Network connectivity issues
- API rate limiting
- Invalid API responses
- Missing dependencies

## Dependencies

- `bash` - Shell interpreter
- `curl` - HTTP requests
- `jq` - JSON parsing
- `nano/vim/vi` - Text editor (for config)

## Troubleshooting

### Common Issues

1. **"Missing required dependencies"**
   - Install curl and jq: `sudo apt install curl jq`

2. **"No API key found"**
   - Get free API key from IPinfo
   - Add to config: `easyip --config`

3. **"Invalid IP address"**
   - Check IP format (IPv4 or IPv6)
   - Ensure no extra characters

4. **"Failed to make API request"**
   - Check internet connectivity
   - Verify API key is valid
   - Check rate limits

### Debug Mode

Use verbose output for debugging:
```bash
easyip 1.1.1.1 --verbose
```

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- [IPinfo](https://ipinfo.io/) for providing the API
- The open source community for inspiration

## Version History

- **v1.0.0** - Initial release with core functionality
  - Basic IP lookup
  - Multiple output formats
  - Caching system
  - Configuration management
  - Map integration 
