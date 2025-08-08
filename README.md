# DrissionPage MCP Server ⚠️ Under Development

[English Version](README.md) | [中文版本](README_CN.md)

⚠️ **This project is currently under active development and is not ready for production use.**

A professional Model Context Protocol (MCP) server that provides browser automation capabilities using DrissionPage. This server enables LLMs to interact with web pages through structured automation tools, bypassing the need for screenshots or visually-tuned models.

## Key Features

- **Fast and lightweight** - Uses DrissionPage's efficient automation engine
- **LLM-friendly** - No vision models needed, operates purely on structured data  
- **Deterministic tool application** - Avoids ambiguity common with screenshot-based approaches
- **14 Web Automation Tools** - Navigate, interact, extract data, and wait operations
- **Professional Architecture** - Follows MCP best practices and modern Python patterns
- **Type Safety** - Full type hints and Pydantic validation

## Requirements

- Python 3.8 or newer
- VS Code, Cursor, Claude Desktop, or any other MCP client

## Getting Started

### Standard Installation

First, install the DrissionPage MCP server with your client.

Standard config works in most MCP tools:

```json
{
  "mcpServers": {
    "drissionpage": {
      "command": "python",
      "args": ["-m", "drissionpage_mcp.cli"]
    }
  }
}
```

### Claude Desktop

Follow the MCP install guide, use the standard config above.

### VS Code

Install the DrissionPage MCP server using the VS Code CLI:

```bash
# For VS Code
code --add-mcp '{"name":"drissionpage","command":"python","args":["-m","drissionpage_mcp.cli"]}'
```

### Manual Installation

1. **Clone and install**:
   ```bash
   git clone https://github.com/your-username/DrissionPageMCP.git
   cd DrissionPageMCP
   pip install -e .
   ```

2. **Configure your MCP client** with the standard config above

3. **Test the installation**:

### Available Tools

#### Navigation Tools
- `page_navigate`: Navigate to a URL
- `page_go_back`: Go back in browser history  
- `page_go_forward`: Go forward in browser history
- `page_refresh`: Refresh current page

#### Page Actions
- `page_resize`: Resize browser window
- `page_screenshot`: Take page screenshots
- `page_click_xy`: Click at specific coordinates
- `page_close`: Close browser
- `page_get_url`: Get current page URL

#### Element Interaction
- `element_find`: Find elements using CSS selectors or XPath
- `element_click`: Click on elements
- `element_type`: Type text into input elements

#### Wait Operations
- `wait_for_element`: Wait for elements to appear
- `wait_time`: Wait for specified time duration

## Installation

### Prerequisites

- Python 3.8 or higher
- Chrome/Chromium browser installed

### Install from source

```bash
# Clone the repository
git clone <repository-url>
cd DrissionPageMCP

# Install in development mode
pip install -e .

# Install development dependencies (optional)
pip install -e ".[dev]"
```

## Quick Start

### 🚀 Launch Server
```bash
# Quick start (recommended)
python start_server.py

# Or use playground
python playground/quick_start.py
```

### 🧪 Test Locally
```bash
# Test without Claude
python playground/local_test.py
```

### 🤖 Use with Claude Code

1. **Start the server** (using command above)
2. **Add to Claude Desktop config**:
   ```json
   {
     "mcpServers": {
       "drissionpage": {
         "command": "python",
         "args": ["-m", "drissionpage_mcp.cli"],
         "cwd": "/path/to/DrissionPageMCP"
       }
     }
   }
   ```
3. **Restart Claude Desktop**
4. **Try commands**:
   ```
   "Navigate to https://example.com and take a screenshot"
   "Click the submit button" 
   "Get all text from the page"
   ```

### 📚 Full Documentation
- [Playground Guide](playground/README.md) - Detailed testing instructions
- [Test Scenarios](playground/test_scenarios/) - Ready-to-use test cases

## Development

### Running Tests

```bash
# Install test dependencies
pip install -e ".[dev]"

# Run tests
python -m pytest tests/

# Run with coverage
python -m pytest tests/ --cov=drissionpage_mcp
```

### Code Quality

```bash
# Format code
black src/ tests/

# Sort imports
isort src/ tests/

# Lint
flake8 src/ tests/

# Type checking
mypy src/
```

## Architecture

The project follows a professional, modular architecture inspired by `playwright-mcp`:

### Core Components
- **`server.py`**: Main MCP server implementation with standard handlers
- **`context.py`**: Browser context and session management
- **`response.py`**: Tool response formatting and content management
- **`cli.py`**: Command-line interface and entry point

### Tool System
- **`tools/base.py`**: Tool definition framework with type safety
- **`tools/navigate.py`**: Navigation and page control tools
- **`tools/common.py`**: Common page actions (screenshot, resize, etc.)
- **`tools/element.py`**: Element interaction tools
- **`tools/wait.py`**: Wait and timing operations

### Key Design Patterns
- **Type-safe tool definitions** using Pydantic schemas
- **Decorator-based tool registration** for clean code organization
- **Standardized tool categorization** (READ_ONLY vs DESTRUCTIVE)
- **Consistent error handling** and response formatting
- **Modular tool loading** for easy extension

## Examples

See `example_usage.py` for detailed usage examples and tool demonstrations.

## Remaining Work

### High Priority

1. **MCP SDK Compatibility**: Update to use the latest MCP Python SDK APIs
2. **Error Handling**: Improve error handling and recovery mechanisms
3. **Browser Management**: Better browser lifecycle management and cleanup
4. **Configuration**: Add configuration options for browser settings, timeouts, etc.

### Medium Priority

5. **Advanced Element Selection**: Support for more complex selectors and element finding strategies
6. **Form Handling**: Dedicated tools for form filling and submission
7. **File Uploads**: Support for file upload operations
8. **Session Management**: Better session persistence and state management
9. **Parallel Operations**: Support for concurrent browser operations
10. **Performance Optimization**: Optimize for faster response times

### Low Priority

11. **Authentication**: Built-in support for common authentication patterns
12. **Proxy Support**: Proxy configuration and rotation
13. **Mobile Emulation**: Mobile device emulation capabilities
14. **Network Interception**: Request/response interception and modification
15. **Advanced Wait Conditions**: More sophisticated wait conditions
16. **Batch Operations**: Support for batch/bulk operations
17. **Plugin System**: Extensible plugin architecture for custom tools
18. **Monitoring/Logging**: Enhanced logging and monitoring capabilities

### Testing & Quality

19. **Integration Tests**: Full end-to-end integration testing with real browsers
20. **Performance Tests**: Performance and load testing
21. **Documentation**: Comprehensive API documentation and user guides
22. **CI/CD**: Automated testing and deployment pipeline

### Known Issues

1. **MCP Server Integration**: Current MCP server implementation may not be fully compatible with the latest MCP protocol
2. **DrissionPage Dependencies**: Requires proper DrissionPage and Chrome installation
3. **Async Operations**: Some operations may not be properly async
4. **Resource Cleanup**: Browser cleanup on server shutdown needs improvement

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests for new functionality
5. Ensure all tests pass
6. Submit a pull request

## License

This project is licensed under the Apache License 2.0. See [LICENSE](LICENSE) for details.

## Acknowledgments

- Built on top of [DrissionPage](https://github.com/g1879/DrissionPage)
- Inspired by [playwright-mcp](https://github.com/microsoft/playwright-mcp)
- Uses the [Model Context Protocol](https://modelcontextprotocol.io/)

## Support

For issues and questions:
1. Check the [GitHub Issues](../../issues)
2. Review the examples in `example_usage.py`
3. Check DrissionPage documentation for browser-specific issues