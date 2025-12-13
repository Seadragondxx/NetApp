# NRSgirls.com Monorepo – AI Coding Agent Instructions

## Project Overview
Private monorepo for NRSgirls.com (DJ + performer live-streaming platform, owned by NRS Group of Fresno)
Contains: web frontend, API backend, infrastructure-as-code, and legal/policy docs

## Architecture & Structure
- **Monorepo**: `/web/` (frontend), `/api/` (backend), `/infra/` (IaC), `/env/` (env configs), legal docs
- **Environment configs**: `/env/development/`, `/env/staging/`, `/env/production/` (never commit secrets; use `.env.example` as template)
- **Component boundaries**: Each service/component in its own directory; cross-cutting code should go in `/shared/` or `/common/` (if present)

## Developer Workflows
- **Build/Test**: Use `mvn -B verify` and `mvn -B test` for builds/tests (see VS Code tasks)
- **Environment setup**: Always add/update env templates in all `/env/{environment}/` dirs when creating new services
- **Deployment**: Ensure correct env configs before deploying; CI/CD integration expected

## Patterns & Conventions
- **Environment variables**: All secrets/API keys via env vars, never hardcoded
- **Frontend**: Supports Next.js, Nuxt.js, Vue, Svelte (see `.gitignore` for clues)
- **Build tools**: Vite, Parcel, webpack (see `.gitignore`)

## Integration Points
- **Live streaming**: Real-time (WebSockets/WebRTC), CDN for video, payment processing for monetization
- **External dependencies**: Streaming providers, payment gateways, auth, CDN/media storage (all via env vars)

## Testing & Quality
- Test in isolated staging before production
- Validate streaming under load
- Security testing for payment/user data

## Windsurf Web Search & Scrape (Firecrawl MCP)

Add web search and scraping to Windsurf using Firecrawl MCP:

1. **Get API Key**: Sign up at [firecrawl.dev/app](https://firecrawl.dev/app) and copy your API key.
2. **Configure**: Add to `./codeium/windsurf/model_config.json`:

```json
{
  "mcpServers": {
    "firecrawl": {
      "command": "npx",
      "args": ["-y", "firecrawl-mcp"],
      "env": {
        "FIRECRAWL_API_KEY": "YOUR_API_KEY"
      }
    }
  }
}
```

Replace `YOUR_API_KEY` with your Firecrawl API key.
3. **Restart Windsurf**. Now Windsurf agents can search and scrape the web.

**Demo queries:**
- `Search for the latest Tailwind CSS features`
- `Scrape firecrawl.dev and explain what it does`
- `Find and scrape the Supabase authentication documentation`

See [https://docs.firecrawl.dev/llms.txt](https://docs.firecrawl.dev/llms.txt) for navigation and more examples.

## AI Agent Quickstart
1. Check which environment (dev/staging/prod) you’re working in
2. Never commit secrets—use `/env/` templates
3. Respect monorepo boundaries and cross-component impacts
4. Reference `README.md` for project/ownership details
5. Ask before major architectural changes
# NRSgirls.com Monorepo - AI Coding Agent Instructions

## Project Overview
This is a private, pre-launch monorepo for NRSgirls.com, a DJ + performer live-streaming platform owned by NRS Group of Fresno. The repository contains web applications, API services, infrastructure configurations, and legal/policy documentation.

## Repository Structure

### Monorepo Organization
- **Intellectual Property**: All code is proprietary and owned by NRS Group of Fresno
- **Components**: The monorepo integrates multiple components:
  - Web frontend (live-streaming interface)
  - API backend services
  - Infrastructure as code (IaC)
  - Legal and policy documentation
  
### Environment Management
- **`/env/development/`**: Development environment configuration templates
- **`/env/staging/`**: Staging environment configuration templates  
- **`/env/production/`**: Production environment configuration templates
- Environment-specific secrets should NEVER be committed (see `.gitignore`)
- Use `.env.example` files as templates, actual `.env` files are git-ignored

## Development Patterns

### Environment Variables
- All environment-specific configs use the `/env/{environment}/` directory structure
- Secrets and API keys must use environment variables, never hardcode them
- The `.gitignore` includes comprehensive exclusions for `.env` and `.env.*` files
- When creating new components, add corresponding environment templates to all three environment directories

### Technology Stack
- **Node.js/JavaScript**: Primary stack based on `.gitignore` patterns (npm, yarn, Node.js artifacts)
- **Frontend Frameworks**: Support for Next.js, Nuxt.js, Vue, Svelte (based on gitignore)
- **Build Tools**: Vite, Parcel, webpack (based on gitignore)
- The exact tech stack may evolve as the monorepo grows

### Critical Workflows

#### Deployment Approach
- Maintain separate configurations for each environment (dev/staging/prod)
- Before deploying, verify environment-specific configs are present in the corresponding `/env/{environment}/` directory
- CI/CD pipeline integration expected (configurations to be added)

#### Adding New Services
1. Create service directory in appropriate location (e.g., `/api/`, `/web/`, `/infra/`)
2. Add environment configurations to `/env/development/`, `/env/staging/`, and `/env/production/`
3. Update `.gitignore` if new build artifacts or cache directories are introduced
4. Document integration points and dependencies

### Security and Legal Requirements

- **All code is proprietary** - no external publication without authorization
- **Privacy-first**: This is a live-streaming platform; handle user data with extreme care
- **Legal compliance**: Changes affecting user data, streaming, or performer contracts may require legal review
- Never expose API keys, database credentials, or streaming service tokens
- Consider DMCA compliance for user-generated content (DJ mixes, performances)

## File and Directory Conventions

### Git Management
- Use descriptive commit messages referencing the component affected (e.g., "api: add user authentication", "web: update streaming UI")
- The `.gitignore` is comprehensive; review it before adding new dependencies or build tools
- `.gitkeep` files maintain empty directory structure across environments

### Code Organization
- Separate concerns: web UI, API logic, infrastructure, and documentation should be clearly demarcated
- Follow monorepo patterns: shared utilities should be accessible across components
- Consider creating a `/shared/` or `/common/` directory for cross-cutting code

## Integration Points

### Live-Streaming Architecture
- Platform integrates DJs and performers with live audience
- Expect real-time components (WebSockets, WebRTC, or similar)
- Consider CDN integration for video streaming
- Payment processing integration for performer monetization likely required

### External Dependencies
- Streaming service providers (to be configured in environment variables)
- Payment gateways (to be configured securely)
- Authentication/identity providers
- CDN and media storage services

## Testing and Quality

- Pre-launch phase: establish testing patterns as components are built
- Test environment-specific configurations in isolated staging environment before production
- Validate streaming performance under load
- Security testing required for payment and user data handling

## Getting Started for AI Agents

1. **Always check the environment**: Determine if you're working on dev, staging, or prod configurations
2. **Respect the monorepo**: Changes should consider cross-component impacts
3. **Security first**: Never commit secrets; always use environment variables from `/env/` templates
4. **Reference README.md**: Core project information and ownership details
5. **Ask before major architectural changes**: This is pre-launch; patterns are still being established
