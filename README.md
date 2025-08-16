# Code Runway

A powerful Raycast extension for developers to quickly search, manage, and launch development projects with Warp terminal integration.

[中文文档](./README_CN.md) | [English](./README.md)

## ✨ Features

- 🔍 **Smart Project Discovery**: Automatically scans and indexes projects in configured directories
- 📂 **Recursive Scanning**: Optionally scan subdirectories to find nested projects.
- 🚀 **Quick Launch**: One-click project startup with customizable Warp terminal configurations
- 🎯 **Project Templates**: Pre-defined launch templates for different development scenarios
- ⭐ **Default Template**: Set your preferred template as default for quick access
- 🛠️ **Custom Commands**: Configure multiple terminal commands with custom working directories
- 📁 **Directory Management**: Easy project directory management with enable/disable controls
- 🎨 **Smart Icons**: Automatically assigns appropriate icons based on project type

## 📋 Requirements

- [Raycast](https://raycast.com/) - Required
- [Warp Terminal](https://www.warp.dev/) - Required for terminal launch functionality

## 🚀 Quick Start

### 1. Configure Project Directories

First, add your project root directories:

1. Open Raycast and search for **"Project Directory Settings"**
2. Click **"Add New Directory"** or press `Cmd + N`
3. Select your project root directories (multiple selection supported)
4. Optional: Add a display name prefix to organize directories

The extension will automatically scan these directories for projects.

### 2. Search and Launch Projects

1. Open Raycast and search for **"Search Projects"**
2. Type to search for your projects
3. Select a project and choose launch method:
   - **Default Template**: Quick launch with your preferred template (if set)
   - **Simple Launch**: Open in a single Warp window
   - **Template Launch**: Choose from available templates

### 3. Manage Templates

Create and customize launch templates:

1. Search for **"Warp Launch Templates"**
2. Create new templates or edit existing ones
3. Set a template as default using the **"Set as Default"** action (`Cmd + D`)

## 🎯 Built-in Templates

The extension comes with a simple default template to get you started. You can customize it or create new ones to fit your needs.

## 🔍 Project Detection

Projects are automatically detected by the presence of these files:

- `package.json` (Node.js/JavaScript)
- `Cargo.toml` (Rust)
- `go.mod` (Go)
- `pom.xml` / `build.gradle` (Java)
- `requirements.txt` / `pyproject.toml` (Python)
- `Gemfile` (Ruby)
- `composer.json` (PHP)
- `.git` (Git repository)
- `Makefile` / `CMakeLists.txt` (C/C++)
- `Dockerfile` (Docker)

## ⌨️ Keyboard Shortcuts

- `Cmd + R`: Refresh project list
- `Cmd + N`: Add new directory (in Directory Settings)
- `Cmd + D`: Set template as default (in Template Management)
- `Enter`: Launch with default template (or simple launch if no default)

## 🔧 Available Commands

| Command | Description |
|---------|-------------|
| **Search Projects** | Search and launch your development projects |
| **Project Directory Settings** | Manage project directories with full controls |
| **Warp Launch Templates** | Create and manage custom launch templates |

## 🎨 Template Customization

### Creating Custom Templates

1. Open **"Warp Launch Templates"**
2. Click **"New Template"**
3. Configure:
   - **Name**: Template identifier
   - **Description**: Brief description
   - **Split Direction**: Vertical (default) or horizontal
   - **Launch Mode**: Split panes, multi-tab, or multi-window
   - **Commands**: Add multiple commands with custom working directories

### Example: Full-stack Template

```yaml
Name: Full-stack Development
Description: Frontend + Backend + Database
Split Direction: Vertical
Commands:
  - Title: Frontend
    Command: npm run dev
    Working Directory: frontend
  - Title: Backend
    Command: npm run dev
    Working Directory: backend
  - Title: Database
    Command: docker-compose up -d && docker-compose logs -f
    Working Directory: (project root)
```

## 🛠️ Warp Integration

The extension leverages Warp's Launch Configuration system:

- Creates YAML configuration files in `~/.warp/launch_configurations/`
- Supports multiple launch modes (split panes, tabs, windows)
- Automatically sets correct working directories
- Handles relative paths within projects

## 🐛 Troubleshooting

### Warp Not Installed

If you see "Warp not installed" error:

1. Download and install [Warp Terminal](https://www.warp.dev/)
2. Ensure Warp is installed in `/Applications/Warp.app`

### Projects Not Found

If projects aren't being detected:

1. **Check file permissions**: Ensure the extension can read directories
2. **Verify project markers**: Confirm projects have detectable files
3. **Test with simple projects**: Create a test directory with `package.json`
4. **Use the diagnostic tool**: Available in project action menus
5. Use `Cmd + R` to refresh the project list

### Launch Failures

If project launch fails:

1. **Check working directories**: Ensure relative paths exist
2. **Test commands manually**: Run commands in terminal first
3. **Use simple commands**: Start with basic commands like `echo` or `ls`
4. **Check Warp configurations**: Look in `~/.warp/launch_configurations/`

### Warp Integration Issues

Common Warp integration problems:

1. **Configuration file creation**: Check if files are created in `~/.warp/launch_configurations/`
2. **URI scheme handling**: Ensure Warp is set as default for `warp://` URLs
3. **Fallback to manual**: If auto-launch fails, manually open Warp and use `Cmd+P` to find configurations

### Template Debugging

If a template isn't working as expected:

1. **Check working directories**: Ensure relative paths exist
2. **Test commands manually**: Run commands in terminal first
3. **Use simple commands**: Start with basic commands like `echo` or `ls`
4. **Check Warp configurations**: Look in `~/.warp/launch_configurations/`

## 🎯 Advanced Template Patterns

### Multi-Environment Development

For projects with multiple environments (dev, staging, prod):

```yaml
Name: Multi-Environment
Description: Dev + Staging + Production monitoring
Commands:
  - Title: Local Development
    Command: npm run dev
    Working Directory: .
  - Title: Staging Deploy
    Command: npm run deploy:staging && npm run logs:staging
    Working Directory: .
  - Title: Production Monitor
    Command: npm run logs:prod
    Working Directory: .
```

### Docker Compose Projects

For complex Docker setups:

```yaml
Name: Docker Full Stack
Description: Complete Docker environment with logs
Commands:
  - Title: Services Up
    Command: docker-compose up -d
    Working Directory: .
  - Title: App Logs
    Command: docker-compose logs -f app
    Working Directory: .
  - Title: Database Logs
    Command: docker-compose logs -f db
    Working Directory: .
  - Title: Redis Logs
    Command: docker-compose logs -f redis
    Working Directory: .
```

### Monorepo Management

For large monorepos with multiple packages:

```yaml
Name: Monorepo Development
Description: Multiple packages in a monorepo
Commands:
  - Title: Root Build Watch
    Command: npm run build:watch
    Working Directory: .
  - Title: Package A
    Command: npm run dev
    Working Directory: packages/package-a
  - Title: Package B
    Command: npm run dev
    Working Directory: packages/package-b
  - Title: Integration Tests
    Command: npm run test:integration
    Working Directory: .
```

## 📁 Directory Organization Tips

### Grouping Projects

Use name prefixes to organize projects by category:

- **Work Projects**: Use prefix "Work-" (e.g., "Work-ClientApp")
- **Personal Projects**: Use prefix "Personal-" 
- **Learning Projects**: Use prefix "Learn-"
- **Open Source**: Use prefix "OSS-"

### Hierarchical Structure

Organize your project directories:

```
~/Development/
├── work/
│   ├── client-projects/
│   └── internal-tools/
├── personal/
│   ├── side-projects/
│   └── experiments/
└── learning/
    ├── tutorials/
    └── courses/
```

Add each category as a separate directory with appropriate prefixes.

## ⚡ Performance Optimization

### Large Directory Handling

For directories with many projects:

1. **Disable unused directories**: Use the enable/disable toggle to exclude directories you don't actively use
2. **Split large directories**: Instead of one huge directory, split into logical subdirectories
3. **Regular cleanup**: Remove outdated projects from scan directories

### Template Efficiency

- **Minimize commands**: Only include essential commands in templates
- **Use relative paths**: Prefer relative working directories over absolute paths
- **Group related commands**: Put related services in the same template

## 🔍 Project Discovery Patterns

### Custom Project Markers

If your projects don't follow standard patterns, you can create marker files:

```bash
# Create a .project file in custom project directories
touch my-custom-project/.project
```

While not automatically detected, this helps you identify projects visually.

### Nested Project Handling

For projects within projects (e.g., monorepos), the scanner will detect:

- Root level projects first
- Subdirectory projects if they have their own project files
- Git submodules as separate projects

## 🎨 Icon Customization Patterns

The extension automatically assigns icons based on project names. To influence icon selection:

- Include technology names in project folders: `my-react-app`, `golang-api`
- Use descriptive names: `mobile-ios-app`, `desktop-electron`
- Organize by type: `api-service`, `web-frontend`

## 🚀 Workflow Optimization

### Daily Development Routine

1. **Morning setup**: Use default template to quickly start your main project
2. **Context switching**: Use specific templates when switching between different types of work
3. **End of day**: Use simple launch to quickly check project status

### Team Collaboration

- **Share templates**: Export template configurations to share with team members
- **Standardize naming**: Use consistent project naming conventions
- **Document patterns**: Create team guidelines for project structure

### Integration with Other Tools

Code Runway works well with:

- **IDE integrations**: Use alongside VS Code or other IDEs
- **Version control**: Git hooks can trigger project rescans
- **CI/CD pipelines**: Templates can include deployment monitoring
- **Task runners**: Integrate with npm scripts, Make, or other build tools

## 📊 Monitoring and Maintenance

### Regular Maintenance Tasks

- **Clean up old configurations**: Remove unused Warp configurations
- **Update templates**: Adjust templates as your workflow evolves
- **Review directory structure**: Reorganize projects as needed
- **Performance check**: Monitor scan times for large directories

### Health Checks

Periodically verify:

- All configured directories are still accessible
- Project detection is working correctly
- Templates launch successfully
- Warp integration is functioning

## 💻 Development

Built with TypeScript and the Raycast API.

```bash
# Development mode
npm run dev

# Build for production
npm run build

# Lint and fix
npm run fix-lint

# Publish to Raycast Store
npm run publish
```

## 📄 License

MIT License - see LICENSE file for details.

---

<div align="center">
  <p>Made with ❤️ for developers who love efficient workflows</p>
  <p>⭐ Star this project if you find it useful!</p>
</div>