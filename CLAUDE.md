# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a Claude Code plugin that provides WordPress-specific agents for building and optimizing WordPress applications. The plugin focuses on REST API endpoint architecture and backend performance optimization.

## Plugin Structure

This repository follows the Claude Code plugin structure with specialized agents:

- **agents/** - Custom Claude agents with specific WordPress expertise
  - `wp-rest-endpoint-architect.md` - Specialized agent for creating clean, maintainable WordPress REST API endpoints
  - `wp-backend-optimizer.md` - Specialized agent for database optimization, caching, and performance tuning
- **commands/** - Custom slash commands (currently empty)
- **skills/** - Reusable skills and workflows (currently empty)
- **hooks/** - Event-driven hooks (currently empty)
- **.claude-plugin/** - Plugin metadata and configuration

## Agent Architecture

### wp-rest-endpoint-architect

This agent implements clean architecture principles for WordPress REST endpoints:

**Key Responsibilities:**
- Design endpoints as thin controllers that delegate to service classes
- Enforce separation of concerns: HTTP handling vs. business logic
- Follow WordPress REST API conventions and standards

**Architectural Patterns:**
- Service layer pattern: `src/Licensing/Services/`
- Repository pattern: `src/Licensing/Repositories/`
- Value objects: `src/Licensing/Value_Objects/`
- Dependency injection using DI container
- Reusable traits for common endpoint functionality

**Endpoint Structure:**
Endpoints should ONLY handle:
- Request validation and sanitization
- Authentication/authorization checks
- Delegating to business logic layers
- Formatting responses
- Error handling and status codes

**Testing Philosophy:**
- Keep endpoint handlers free of direct database queries
- Use dependency injection for all services
- Avoid mocks; insert test data directly into database
- Write integration tests for endpoint behavior

### wp-backend-optimizer

This agent focuses on WordPress performance optimization while maintaining code readability:

**Core Expertise:**
- Database query optimization (EXPLAIN analysis, indexing, query structure)
- Caching strategies (transients, object caching, memoization)
- Efficient data structures balancing performance and maintainability
- High-traffic WordPress scalability

**Optimization Strategies:**
1. **Memoization**: Static variables, class properties, WordPress transients
2. **Database**: Query analysis, efficient table structures, batch operations, strategic JOINs
3. **Data Structures**: Value objects, DTOs, repository patterns, minimal memory footprint

**Development Philosophy:**
- Readable, maintainable code over clever optimizations
- Profile first, optimize second
- Measure impact with benchmarks
- Document performance-critical sections
- Avoid premature optimization and micro-optimizations

## WordPress Development Standards

Both agents enforce:
- WordPress coding standards
- SOLID design principles
- Security best practices (nonce verification, input sanitization, capability checks)
- Self-documenting code with meaningful names
- Type hints and PHPDoc blocks
- Separation of concerns and modularity

## Using This Plugin

When working on WordPress projects with Claude Code:

1. The agents will be automatically available through the Task tool
2. The `wp-rest-endpoint-architect` agent is proactively invoked for REST endpoint work
3. The `wp-backend-optimizer` agent is proactively invoked for performance optimization tasks
4. Both agents analyze existing codebase patterns before making recommendations
5. Architectural decisions are documented inline with comments explaining the "why"

## Testing Approach

- Integration tests preferred over unit tests with heavy mocking
- Test data inserted directly into database rather than using mocks
- Focus on testing behavior, not implementation details
- Keep business logic testable by maintaining separation from WordPress APIs
