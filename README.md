# WordPress Plugin for Claude Code

A [Claude Code](https://claude.ai/code) plugin that provides specialized agents for WordPress development, focusing on clean architecture, REST API design, and performance optimization.

## Overview

This plugin enhances Claude Code with WordPress-specific expertise through two specialized agents:

- **wp-rest-endpoint-architect** - Expert in building clean, maintainable WordPress REST API endpoints
- **wp-backend-optimizer** - Expert in WordPress performance optimization and database efficiency

## Installation

### Using Claude Code Plugin Manager

```bash
# From within Claude Code, run:
/plugin install borkweb/claude-wordpress-plugin
```

### Manual Installation

1. Clone this repository into your Claude Code plugins directory:
```bash
cd ~/.claude/plugins
git clone https://github.com/borkweb/claude-wordpress-plugin wp
```

2. Restart Claude Code or reload your configuration

## Agents

### wp-rest-endpoint-architect

**Purpose:** Create WordPress REST API endpoints that follow clean architecture principles.

**When to use:**
- Creating new REST API endpoints
- Reviewing existing endpoint implementations
- Refactoring endpoints to improve maintainability
- Implementing API versioning strategies

**Key principles:**
- Endpoints act as thin controllers
- Business logic lives in service classes
- Data access through repository pattern
- Dependency injection for testability
- Separation of HTTP concerns from domain logic

**Architectural patterns enforced:**
```
src/
├── Services/         # Business logic layer
├── Repositories/     # Data access layer
└── Value_Objects/    # Data integrity and validation
```

**Example usage:**
```
Create a REST endpoint for managing product inventory with proper validation
```

The agent will design an endpoint that:
- Validates and sanitizes requests
- Delegates to a `Product_Service` for business logic
- Uses a `Product_Repository` for data access
- Returns proper HTTP status codes and formatted responses

### wp-backend-optimizer

**Purpose:** Optimize WordPress backend code for performance while maintaining code quality.

**When to use:**
- Slow database queries or repeated queries
- Implementing caching strategies
- Optimizing data structures
- Refactoring for better performance
- Analyzing and improving query efficiency

**Optimization strategies:**
- **Memoization:** In-request caching with static variables, cross-request with transients
- **Database:** Query analysis with EXPLAIN, strategic indexing, batch operations
- **Data structures:** Efficient designs balancing performance and readability

**Development philosophy:**
- Profile before optimizing
- Measure impact with benchmarks
- Readable code over clever optimizations
- Document performance-critical decisions

**Example usage:**
```
This function makes multiple database calls in a loop - can you optimize it?
```

The agent will:
1. Analyze the query patterns
2. Implement memoization or caching where appropriate
3. Suggest database structure improvements if needed
4. Balance performance gains with code maintainability

## Agent Integration

Both agents are automatically available when working on WordPress projects:

- Invoked **proactively** by Claude Code when relevant tasks are detected
- Can be explicitly called using the Task tool
- Follow WordPress coding standards and best practices
- Provide detailed architectural explanations

## Development Standards

Both agents enforce:

✅ WordPress coding standards
✅ SOLID design principles
✅ Security best practices (nonce verification, sanitization, capability checks)
✅ Type hints and PHPDoc blocks
✅ Separation of concerns
✅ Integration testing over heavy mocking

## Testing Philosophy

- **Avoid mocking:** Insert actual test data into the database
- **Test behavior, not implementation:** Focus on what the code does, not how
- **Keep business logic testable:** Maintain separation from WordPress APIs
- **Integration tests preferred:** Test real interactions between components

## Example Workflow

When building a WordPress feature with these agents:

1. **Design phase:** wp-rest-endpoint-architect helps structure your API endpoints
2. **Implementation:** Agents guide separation of concerns (endpoint → service → repository)
3. **Optimization:** wp-backend-optimizer identifies and resolves performance bottlenecks
4. **Testing:** Agents recommend integration test strategies

## Contributing

Contributions are welcome! Please feel free to submit issues or pull requests.

## License

MIT License - see [LICENSE](LICENSE) file for details.

## Author

Matthew Batchelder ([@borkweb](https://github.com/borkweb))

## Links

- [Claude Code](https://claude.ai/code)
- [Plugin Repository](https://github.com/borkweb/claude-wordpress-plugin)
- [Report Issues](https://github.com/borkweb/claude-wordpress-plugin/issues)
