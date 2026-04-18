# Homebrew Tap for Tingly-Box

This repository contains the Homebrew formula for installing [Tingly-Box](https://github.com/tingly-dev/tingly-box).

## Quick Start

```bash
# Tap the repository
brew tap tingly-dev/homebrew-tingly

# Install tingly-box
brew install tingly-box

# Use the full command or alias
tingly-box start
# or
tb start
```

> **Note**: Homebrew internally references this as `tingly-dev/tap` (the `homebrew-` prefix is automatically stripped). You may see this name in installation output.

## Update

```bash
brew upgrade tingly-box
```

## Uninstall

```bash
brew uninstall tingly-box
brew untap tingly-dev/homebrew-tingly
```

## Automated Release Process

This homebrew tap is **manually controlled** in this repository. When you need to update to a new release:

### Quick Update (Recommended)

1. Go to [Actions → Update Formula](https://github.com/tingly-dev/homebrew-tingly/actions/workflows/update-formula.yml)
2. Click "Run workflow"
3. Enter the release tag (e.g., `v0.260124.900`)
4. Click "Run workflow"

The workflow will:
- Fetch the release from [tingly-box](https://github.com/tingly-dev/tingly-box)
- Download all platform binaries
- Calculate SHA256 hashes
- Generate and commit the formula

### Update with Pull Request

For better control, create a PR first:

1. Run the workflow with "Create PR" enabled
2. Review the generated formula
3. Merge when ready

### Command Line Update

```bash
# Trigger update via GitHub CLI
gh workflow run update-formula.yml \
  --repo tingly-dev/homebrew-tingly \
  -f tag="v0.260124.900"

# Or with PR
gh workflow run update-formula.yml \
  --repo tingly-dev/homebrew-tingly \
  -f tag="v0.260124.900" \
  -f create_pr=true
```

### Supported Platforms

| Platform | Architecture          | Binary Name              |
| -------- | --------------------- | ------------------------ |
| macOS    | ARM64 (Apple Silicon) | `tingly-box-macos-arm64` |
| macOS    | AMD64 (Intel)         | `tingly-box-macos-amd64` |
| Linux    | AMD64 (x86_64)        | `tingly-box-linux-amd64` |
| Linux    | ARM64 (aarch64)       | `tingly-box-linux-arm64` |

## Development

### Local Formula Generation

To generate the formula locally for testing:

```bash
# Set the version
export VERSION="v0.260.124.900"

# Download and calculate hashes (optional - for testing)
curl -LO https://github.com/tingly-dev/tingly-box/releases/download/${VERSION}/tingly-box-macos-arm64.zip
SHA_DARWIN_ARM64=$(shasum -a 256 tingly-box-macos-arm64.zip | awk '{print $1}')
# Repeat for other platforms...

# Generate formula
ruby Formula/generate.rb \
  VERSION=${VERSION} \
  SHA256_DARWIN_ARM64=${SHA_DARWIN_ARM64} \
  SHA256_DARWIN_AMD64=${SHA_DARWIN_AMD64} \
  SHA256_LINUX_AMD64=${SHA_LINUX_AMD64} \
  SHA256_LINUX_ARM64=${SHA_LINUX_ARM64}
```

### Manual Formula Update

If you need to manually update the formula:

1. Go to the [Actions tab](https://github.com/tingly-dev/homebrew-tingly/actions)
2. Select "Update Formula on Release" workflow
3. Click "Run workflow"
4. Enter the release tag (e.g., `v0.260.124.900`)
5. Click "Run workflow"

### Testing Formula Changes

To test formula changes before committing:

```bash
# Install from local file
brew install --build-from-source Formula/tingly-box.rb

# Or install from a specific branch
brew install tingly-dev/homebrew-tingly/tingly-box
```

## Project Structure

```
.
├── .github/
│   └── workflows/
│       └── update-formula.yml    # Automated update workflow
├── Formula/
│   ├── tingly-box.rb             # Generated formula (DO NOT EDIT)
│   ├── generate.rb               # Formula generation script
│   └── README.md                 # Formula documentation
├── README.md                     # This file
└── LICENSE
```

## Troubleshooting

### Formula Not Updating

If the formula doesn't update after a release:

1. Check the [Actions tab](https://github.com/tingly-dev/homebrew-tingly/actions) for failed runs
2. Verify the release exists in the [tingly-box releases](https://github.com/tingly-dev/tingly-box/releases)
3. Ensure all required assets are present in the release
4. Manually trigger the update workflow if needed

### Installation Issues

If you encounter issues during installation:

```bash
# Debug installation
brew install --verbose --debug tingly-dev/homebrew-tingly/tingly-box

# Check formula
brew info tingly-dev/homebrew-tingly/tingly-box

# View installed files
brew list tingly-box
```

## Contributing

This repository is primarily automated. Changes to the formula should be made through the release process in the main [tingly-box repository](https://github.com/tingly-dev/tingly-box).

For issues or suggestions:
- Open an issue in this repository
- Open an issue in the [tingly-box repository](https://github.com/tingly-dev/tingly-box/issues)

## License

This project follows the same license as [Tingly-Box](https://github.com/tingly-dev/tingly-box).
