# Contributing to Tingly-Box Homebrew Tap

Thank you for your interest in contributing! This document provides guidelines for contributing to the Tingly-Box Homebrew tap.

## Overview

This repository is primarily automated and receives updates from the [Tingly-Box release workflow](https://github.com/tingly-dev/tingly-box). Most formula updates happen automatically without manual intervention.

## How Formula Updates Work

### Automated Process

1. A release is created in the [tingly-box repository](https://github.com/tingly-dev/tingly-box)
2. The release workflow triggers `update-formula.yml` in this repository
3. The workflow:
   - Downloads all platform binaries
   - Calculates SHA256 hashes
   - Runs `Formula/generate.rb` to create the formula
   - Commits and pushes the updated formula

### Manual Updates

If you need to manually update the formula:

```bash
# Trigger the workflow via GitHub CLI
gh workflow run update-formula.yml \
  --repo tingly-dev/homebrew-tingly \
  -f tag="v0.260.124.900"
```

Or use the GitHub UI:
1. Go to Actions → Update Formula on Release
2. Click "Run workflow"
3. Enter the release tag
4. Click "Run workflow"

## Development Workflow

### Setting Up Development Environment

```bash
# Clone the repository
git clone https://github.com/tingly-dev/homebrew-tingly.git
cd tap

# Install dependencies (none required for formula generation)

# Test local formula generation
ruby Formula/generate.rb VERSION=v0.260.124.900
```

### Making Changes

1. **Formula Generation Script** (`Formula/generate.rb`):
   - Modify the formula template as needed
   - Test locally before committing
   - Ensure all platforms are supported

2. **Update Workflow** (`.github/workflows/update-formula.yml`):
   - Add new platform support if needed
   - Update validation rules
   - Test workflow changes in a feature branch

3. **Documentation**:
   - Keep README.md up to date
   - Document any new features or processes
   - Update troubleshooting guides

### Testing Changes

#### Testing Formula Locally

```bash
# Install from local formula file
brew install --build-from-source Formula/tingly-box.rb

# Test the installation
tingly-box version
tingly-box start

# Uninstall when done
brew uninstall tingly-box
```

#### Testing Workflow Changes

1. Create a feature branch
2. Make your changes
3. Push the branch
4. Test the workflow manually
5. Create a pull request

## Platform Support

When adding support for new platforms:

1. Update `Formula/generate.rb` to include the new platform
2. Update `.github/workflows/update-formula.yml` to download and hash the new binary
3. Update the `install` method to handle the new platform
4. Test the formula on the target platform

### Current Platforms

- macOS ARM64 (Apple Silicon)
- macOS AMD64 (Intel)
- Linux AMD64 (x86_64)
- Linux ARM64 (aarch64)

## Release Process

### Versioning

The formula version follows the release tags from the main repository:
- Format: `v<major>.<minor>.<patch>-<build>`
- Example: `v0.260.124.900`

### Before Creating a Release

1. Ensure all platform binaries are built successfully
2. Verify all release assets are uploaded
3. Check that SHA256 hashes are correct
4. Test the formula locally if possible

### After a Release

1. Monitor the `update-formula.yml` workflow
2. Verify the formula is updated correctly
3. Test installation from the tap
4. Update documentation if needed

## Code Style

### Ruby (Formula)

- Follow [Ruby Style Guide](https://rubystyle.guide/)
- Use 2 spaces for indentation
- Keep lines under 100 characters
- Add comments for complex logic

### YAML (Workflows)

- Follow [YAML syntax](https://yaml.org/spec/)
- Use 2 spaces for indentation
- Add comments for workflow steps
- Keep jobs focused and modular

## Pull Request Process

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### PR Guidelines

- Describe the motivation for the change
- List the changes made
- Include screenshots if applicable
- Mention any breaking changes
- Link related issues

## Issues and Bug Reports

When reporting issues:

1. Use the issue templates
2. Provide system information:
   - macOS/Linux version
   - Homebrew version (`brew --version`)
   - Formula version (`brew info tingly-dev/homebrew-tingly/tingly-box`)
3. Include error messages and logs
4. Describe steps to reproduce

## Community Guidelines

- Be respectful and constructive
- Focus on what is best for the community
- Show empathy towards other community members

## Getting Help

- Check existing [Issues](https://github.com/tingly-dev/homebrew-tingly/issues)
- Review [Documentation](https://github.com/tingly-dev/tingly-box)
- Join community discussions (if available)

## Resources

- [Homebrew Formula Cookbook](https://docs.brew.sh/Formula-Cookbook)
- [Homebrew Python for Formula Authors](https://docs.brew.sh/Python-for-Formula-Authors)
- [Tingly-Box Documentation](https://github.com/tingly-dev/tingly-box)

## License

By contributing, you agree that your contributions will be licensed under the same license as the project.
