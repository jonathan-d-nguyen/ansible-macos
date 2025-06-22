<!-- Improved compatibility of back to top link: See: https://github.com/othneildrew/Best-README-Template/pull/73 -->

<!--
*** Thanks for checking out this macOS Development Environment automation project.
*** If you have a suggestion that would make this better, please fork the repo
*** and create a pull request or simply open an issue with the tag "enhancement".
*** Don't forget to give the project a star!
*** Thanks again! Now go create something AMAZING! :D
-->

<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<!-- PROJECT LOGO -->
<br />
<div align="center">

<h3 align="center">macOS Development Environment</h3>

  <p align="center">
    Automated macOS system configuration and application deployment using Ansible. Streamlines migration from existing MacBook or fresh system setup with curated development tools, applications, and system preferences.
    <br />
    <a href="https://github.com/jonathan-d-nguyen/ansible-macos"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/jonathan-d-nguyen/ansible-macos/issues/new?labels=bug&template=bug-report---.md">Report Bug</a>
  </p>
</div>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#1-about-the-project">About The Project</a>
      <ul>
        <li><a href="#11-built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#2-quick-start">Quick Start</a>
      <ul>
        <li><a href="#21-prerequisites">Prerequisites</a></li>
        <li><a href="#22-development-environment-settings">Development Environment Settings</a></li>
        <li><a href="#23-basic-setup">Basic Setup</a></li>
      </ul>
    </li>
    <li>
      <a href="#3-deployment--operations">Deployment & Operations</a>
      <ul>
        <li><a href="#31-full-installation-steps">Full Installation Steps</a></li>
        <li><a href="#32-configuration-options">Configuration Options</a></li>
        <li><a href="#33-system-analysis-tools">System Analysis Tools</a></li>
        <li><a href="#34-troubleshooting">Troubleshooting</a></li>
        <li><a href="#35-advanced-usage">Advanced Usage</a></li>
      </ul>
    </li>
    <li><a href="#4-roadmap">Roadmap</a></li>
    <li>
      <a href="#5-contributing">Contributing</a>
      <ul>
        <li><a href="#51-top-contributors">Top Contributors</a></li>
      </ul>
    </li>
    <li><a href="#6-license">License</a></li>
    <li><a href="#7-contact">Contact</a></li>
    <li><a href="#8-acknowledgments">Acknowledgments</a></li>
  </ol>
</details>

<!-- Back to top link template for use throughout document -->

<a id="readme-top"></a>

<!-- ABOUT THE PROJECT -->

## 1. About The Project

This repository demonstrates Infrastructure as Code practices for macOS system configuration using Ansible. It provides automated deployment of development tools, applications, system preferences, and configuration files, enabling consistent development environments across multiple machines or streamlined migration between systems.

**Key Features:**

- **Selective Deployment**: Choose which components to install/configure
- **System Migration**: Automated migration from existing MacBook to new system
- **Development Environment**: Rapid deployment of development tools and configurations
- **Consistency**: Maintain identical configurations across multiple machines
- **180+ Applications**: Comprehensive package management via Homebrew

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### 1.1. Built With

- [![Ansible][Ansible.com]][Ansible-url]
- [![Homebrew][Homebrew.sh]][Homebrew-url]
- [![Shell Script][Shell Script Badge]][Shell-url]
- [![YAML][YAML Badge]][YAML-url]
- [![macOS][macOS Badge]][macOS-url]
- [![Git][Git Badge]][Git-url]
- [![Docker][Docker.io]][Docker-url]
- [![VS Code][VS Code Badge]][VSCode-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- QUICK START -->

## 2. Quick Start

Get up and running quickly with these basic steps. For detailed instructions, see [Full Installation Steps](#31-full-installation-steps).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### 2.1. Prerequisites

1. **macOS Requirements**

   - macOS 12.0+ (Monterey or later)
   - Administrator access
   - Internet connection

2. **Ansible Installation**

   ```sh
   # Install via Homebrew (recommended)
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   brew install ansible

   # Or install via pip
   pip3 install ansible
   ```

3. **Homebrew Installation**

   ```sh
   # Install Homebrew (if not already installed)
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### 2.2. Development Environment Settings

#### Project Structure

```
ansible-macos/
├── ansible/
│   ├── inventory/
│   │   ├── group_vars/
│   │   │   ├── all.yml                    # Main configuration variables
│   │   │   ├── all-comprehensive.yml      # Extended configuration options
│   │   │   ├── enhanced-preferences.yml   # Advanced system preferences
│   │   │   └── minimal.yml               # Minimal installation profile
│   │   └── hosts.yml                     # Ansible inventory
│   └── playbooks/
│       ├── main.yml                      # Master orchestration playbook
│       ├── homebrew.yml                  # Package management
│       ├── dotfiles.yml                  # Shell configuration sync
│       ├── system-prefs.yml              # macOS system preferences
│       ├── enhanced-system-prefs.yml     # Advanced system configuration
│       └── deploy-priority.yml           # Priority deployment sequence
├── config/
│   └── dotfiles/                         # Shell configs, Git settings, SSH configs
├── scripts/
│   ├── deploy-config.sh                  # Interactive deployment script
│   ├── system_inventory.sh               # System analysis and discovery
│   ├── macos_software_audit.sh          # Software inventory generation
│   └── preference-management.sh          # System preference utilities
├── docs/
│   ├── Manual_Installation_Guide.md      # Non-automatable software guide
│   ├── macos-ssh-setup.md               # SSH configuration guide
│   └── ssh_host_key_verification.md     # SSH security documentation
└── setup.sh                             # Initial project setup
```

#### Configuration Profiles

The project includes multiple configuration profiles for different use cases:

| Profile                      | Purpose                | Applications      | System Prefs    | Use Case                       |
| ---------------------------- | ---------------------- | ----------------- | --------------- | ------------------------------ |
| **minimal.yml**              | Essential tools only   | ~30 core apps     | Basic settings  | Quick setup, minimal footprint |
| **all.yml**                  | Standard deployment    | ~180 applications | Standard prefs  | Full development environment   |
| **all-comprehensive.yml**    | Complete feature set   | All applications  | All preferences | Maximum functionality          |
| **enhanced-preferences.yml** | Advanced customization | Standard apps     | Advanced tweaks | Power user setup               |

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### 2.3. Basic Setup

1. **Clone and prepare**

   ```sh
   git clone https://github.com/jonathan-d-nguyen/ansible-macos.git
   cd ansible-macos

   # Run initial setup
   ./setup.sh
   ```

2. **Interactive deployment**

   ```sh
   # Launch interactive deployment script
   ./scripts/deploy-config.sh
   ```

3. **Quick deployment (all components)**
   ```sh
   cd ansible
   ansible-playbook -i inventory/hosts.yml playbooks/main.yml
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- DEPLOYMENT & OPERATIONS -->

## 3. Deployment & Operations

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### 3.1. Full Installation Steps

1. **Repository Setup**

   ```sh
   git clone https://github.com/jonathan-d-nguyen/ansible-macos.git
   cd ansible-macos
   ./setup.sh
   ```

2. **Interactive Component Selection**

   ```sh
   # Launch interactive deployment
   ./scripts/deploy-config.sh
   ```

   The script will prompt you to select components:

   - **homebrew**: Package manager and command-line tools (git, node, fzf, fd, powershell)
   - **apps**: GUI applications via Homebrew Cask (VS Code, Docker, Alfred, Obsidian, Slack, etc.)
   - **system**: macOS system preferences (Dock, Finder, keyboard settings)
   - **dotfiles**: Shell configurations (.zshrc, .gitconfig, .bash_profile, etc.)
   - **keyboard-maestro**: Macro automation import
   - **alfred**: Workflow and preference import

3. **Manual Deployment (Advanced)**

   ```sh
   cd ansible

   # Deploy specific components
   ansible-playbook -i inventory/hosts.yml --tags "homebrew,dotfiles" playbooks/main.yml

   # Deploy with specific profile
   ansible-playbook -i inventory/hosts.yml -e @inventory/group_vars/minimal.yml playbooks/main.yml

   # Deploy everything
   ansible-playbook -i inventory/hosts.yml playbooks/main.yml
   ```

4. **Verification**

   ```sh
   # Check installed packages
   brew list

   # Verify system preferences
   defaults read com.apple.dock

   # Test dotfiles
   source ~/.zshrc
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### 3.2. Configuration Options

#### Main Configuration: `ansible/inventory/group_vars/all.yml`

```yaml
# Core packages
homebrew_packages:
  - git
  - node
  - fzf
  - fd
  - powershell
  - jsonnet

# GUI applications
homebrew_casks:
  # Development Tools
  - visual-studio-code
  - docker
  - iterm2
  - github-desktop
  - fork

  # Productivity
  - alfred
  - keyboard-maestro
  - obsidian
  - rectangle

# System preferences
system_preferences:
  - { domain: "com.apple.dock", key: "autohide", type: "bool", value: true }
  - { domain: "com.apple.dock", key: "tilesize", type: "int", value: 48 }
  - {
      domain: "com.apple.finder",
      key: "AppleShowAllExtensions",
      type: "bool",
      value: true,
    }

# Dotfiles to sync
dotfiles:
  - src: ".zshrc"
    dest: "~/.zshrc"
  - src: ".gitconfig"
    dest: "~/.gitconfig"
```

#### Feature Toggles

Control deployment scope in `main.yml`:

```yaml
vars:
  install_homebrew: true
  install_apps: true
  configure_system: true
  sync_dotfiles: true
  import_keyboard_maestro: false
  import_alfred: false
```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### 3.3. System Analysis Tools

1. **Generate Software Inventory**

   ```sh
   # Create inventory of currently installed software
   ./scripts/macos_software_audit.sh

   # Generate system configuration inventory
   ./scripts/system_inventory.sh
   ```

2. **Export Current Dotfiles**

   ```sh
   # Export current shell configurations for version control
   ./scripts/export-dotfiles.sh
   ```

3. **System Preference Discovery**

   ```sh
   # Discover current system preferences
   ./scripts/discover-preferences.sh
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### 3.4. Troubleshooting

1. **Common Issues**

   ```sh
   # Homebrew permission errors
   sudo chown -R $(whoami) /opt/homebrew

   # System preferences not applied
   # Log out and back in, or restart

   # SSH key issues
   ssh-add -K ~/.ssh/id_rsa
   ```

2. **Debug Mode**

   ```sh
   # Run with verbose output
   ansible-playbook -i inventory/hosts.yml -vvv playbooks/main.yml
   ```

3. **Reset to Defaults**
   - System preferences: Reset via System Preferences app
   - Homebrew packages: `brew uninstall <package>`
   - Applications: Drag to Trash or use App Cleaner

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### 3.5. Advanced Usage

1. **Custom Playbook Development**

   ```sh
   # Create custom playbook for specific workflows
   ansible-playbook -i inventory/hosts.yml playbooks/your-custom-playbook.yml
   ```

2. **Profile-Based Deployment**

   ```sh
   # Use different configuration profiles
   ansible-playbook -i inventory/hosts.yml -e @inventory/group_vars/minimal.yml playbooks/main.yml
   ```

3. **Adding New Applications**

   Edit `ansible/inventory/group_vars/all.yml`:

   ```yaml
   homebrew_casks:
     - existing-app
     - your-new-app # Add new applications here
   ```

4. **Custom System Preferences**

   ```yaml
   system_preferences:
     - {
         domain: "com.apple.yourapp",
         key: "setting",
         type: "bool",
         value: true,
       }
   ```

<!-- _For more examples, please refer to the [Documentation](docs/)_ -->

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ROADMAP -->

## 4. Roadmap

- [ ] **Enhanced Documentation**

  - [ ] Video walkthrough of deployment process
  - [ ] Troubleshooting guide expansion
  - [ ] Performance optimization guide

- [ ] **Extended Platform Support**

  - [ ] Linux compatibility layer
  - [ ] Windows WSL support consideration
  - [ ] Cross-platform dotfile management

- [ ] **Advanced Features**

  - [ ] mas-cli integration for Mac App Store applications
  - [ ] Custom download scripts for non-Homebrew applications
  - [ ] Ansible Vault integration for sensitive configurations
  - [ ] Role-based deployment (developer, designer, manager profiles)

- [x] **Core Infrastructure**

  - [x] Selective component deployment
  - [x] Interactive deployment script
  - [x] Multiple configuration profiles
  - [x] System analysis and inventory tools
  - [x] Comprehensive application coverage (180+ apps)
  - [x] Dotfile synchronization
  - [x] System preference automation

- [x] **Documentation & Guides**
  - [x] Manual installation guide for non-automatable software
  - [x] SSH setup and security documentation
  - [x] System preference management utilities

See the [open issues](https://github.com/jonathan-d-nguyen/ansible-macos/issues) for a full list of proposed features (and known issues).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTRIBUTING -->

## 5. Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Test changes on clean system or VM
4. Update documentation as needed
5. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
6. Push to the Branch (`git push origin feature/AmazingFeature`)
7. Open a Pull Request

### Testing Guidelines

- Test on clean macOS installation when possible
- Verify idempotency (running twice should be safe)
- Document any new requirements or dependencies

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### 5.1. Top contributors:

<a href="https://github.com/jonathan-d-nguyen/ansible-macos/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=jonathan-d-nguyen/ansible-macos" alt="contrib.rocks image" />
</a>

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- LICENSE -->

## 6. License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTACT -->

## 7. Contact

Jonathan Nguyen - jonathan@jdnguyen.tech

Project Link: [https://github.com/jonathan-d-nguyen/ansible-macos](https://github.com/jonathan-d-nguyen/ansible-macos)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ACKNOWLEDGMENTS -->

## 8. Acknowledgments

- [Awesome README Template](https://github.com/othneildrew/Best-README-Template/)
- [Ansible Community](https://www.ansible.com/community) - For the automation framework
- [Homebrew](https://brew.sh/) - For simplified macOS package management
- [macOS Community](https://developer.apple.com/macos/) - For system preference documentation and best practices

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->

[contributors-shield]: https://img.shields.io/github/contributors/jonathan-d-nguyen/ansible-macos.svg?style=for-the-badge
[contributors-url]: https://github.com/jonathan-d-nguyen/ansible-macos/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/jonathan-d-nguyen/ansible-macos.svg?style=for-the-badge
[forks-url]: https://github.com/jonathan-d-nguyen/ansible-macos/network/members
[stars-shield]: https://img.shields.io/github/stars/jonathan-d-nguyen/ansible-macos.svg?style=for-the-badge
[stars-url]: https://github.com/jonathan-d-nguyen/ansible-macos/stargazers
[issues-shield]: https://img.shields.io/github/issues/jonathan-d-nguyen/ansible-macos.svg?style=for-the-badge
[issues-url]: https://github.com/jonathan-d-nguyen/ansible-macos/issues
[license-shield]: https://img.shields.io/github/license/jonathan-d-nguyen/ansible-macos.svg?style=for-the-badge
[license-url]: https://github.com/jonathan-d-nguyen/ansible-macos/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/JonathanDanhNguyen
[product-screenshot]: images/screenshot.png
[Ansible.com]: https://img.shields.io/badge/ansible-%231A1918.svg?style=for-the-badge&logo=ansible&logoColor=white
[Ansible-url]: https://www.ansible.com/
[Homebrew.sh]: https://img.shields.io/badge/Homebrew-FBB040?style=for-the-badge&logo=homebrew&logoColor=black
[Homebrew-url]: https://brew.sh/
[Shell Script Badge]: https://img.shields.io/badge/shell_script-%23121011.svg?style=for-the-badge&logo=gnu-bash&logoColor=white
[Shell-url]: https://www.gnu.org/software/bash/
[YAML Badge]: https://img.shields.io/badge/yaml-%23ffffff.svg?style=for-the-badge&logo=yaml&logoColor=151515
[YAML-url]: https://yaml.org/
[macOS Badge]: https://img.shields.io/badge/mac%20os-000000?style=for-the-badge&logo=macos&logoColor=F0F0F0
[macOS-url]: https://www.apple.com/macos/
[Git Badge]: https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white
[Git-url]: https://git-scm.com/
[Docker.io]: https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white
[Docker-url]: https://www.docker.com/
[VS Code Badge]: https://img.shields.io/badge/Visual%20Studio%20Code-0078d4.svg?style=for-the-badge&logo=visual-studio-code&logoColor=white
[VSCode-url]: https://code.visualstudio.com/
