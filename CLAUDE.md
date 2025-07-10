# Documentation for Meteora

## Working relationship

- You can push back on ideas-this can lead to better documentation. Cite sources and explain your reasoning when you do so
- ALWAYS ask for clarification rather than making assumptions
- NEVER lie, guess, or make up information

## Project context

### Documentation purpose

Meteora builds liquidity pools and DeFi infrastructure on Solana. This documentation serves:

- Developers integrating Meteora's products
- Projects launching tokens using Meteora's pools
- Users understanding Meteora's products
- Partners building on top of Meteora's infrastructure

### Technical products

Core products documented:

- **DLMM (Dynamic Liquidity Market Maker)**: Concentrated liquidity with bin-based architecture, dynamic fees, zero-slippage bins
- **DAMM v1 & v2 (Dynamic AMM)**: Constant product AMMs with different feature sets
- **DBC (Dynamic Bonding Curve)**: Customizable virtual curves for token launches
- **Dynamic Vault**: Yield optimization infrastructure that rebalances across lending platforms
- **Alpha Vault**: Anti-sniper mechanism for token launches
- **Anti-Sniper Suite (A.S.S.)**: Fee scheduler, rate limiter, and other anti-bot tools

### Documentation structure

- Format: MDX files with YAML frontmatter
- Config: docs.json for navigation, theme, settings
- Components: Mintlify components (Card, CardGroup, Steps, Note, Warning, Info, etc.)
- Organization:
  - `/overview` - Product overviews and concepts
  - `/developer-guide` - Integration guides and technical docs
  - `/anti-sniper-suite` - Anti-bot toolkit documentation
  - `/legal` - Terms of service
  - `/resources` - Community tools and dashboards

## Content strategy

- Document just enough for user success - not too much, not too little
- Prioritize accuracy and usability of information
- Make content evergreen when possible
- Search for existing information before adding new content. Avoid duplication unless it is done for a strategic reason
- Check existing patterns for consistency
- Start by making the smallest reasonable changes

## Meteora-specific conventions

### Technical terminology

Use these terms consistently:

- "Launch Pool" not "launch pool" when referring to the product
- "Dynamic AMM" or "DAMM" not "dynamic amm"
- "DLMM" not "dlmm" or "Dlmm"
- "Alpha Vault" not "alpha vault"
- "Anti-Sniper Suite" or "A.S.S." for the toolkit
- "liquidity provider" or "LP" for users providing liquidity
- "position" for LP holdings in pools
- "bin" for DLMM price ranges
- "permissionless" not "permission-less"

### Code patterns

TypeScript SDK initialization pattern:

```typescript
import { Connection } from "@solana/web3.js";
import { ClientName } from "@meteora-ag/sdk-name";

const connection = new Connection("https://api.mainnet-beta.solana.com");
const client = new ClientName(connection);
```

### Program IDs

Always use mainnet program IDs in examples unless specifically for devnet:

- DLMM: `LBUZKhRxPF3XUpBCjp4YzTKgLccjZhTSDM9YuVaPwxo`
- DAMM v1: `Eo7WjKq67rjJQSZxS6z3YkapzY3eMj6Xy8X5EQVn5UaB`
- DAMM v2: `cpamdpZCGKUy5JxQXB4dcpGPiikHawvSWAd6mEn1sGG`
- DBC: `dbcij3LWUppWqq96dh6gJWwBifmcGfLSB5D4DuSMaqN`
- Dynamic Vault: `24Uqj9JCLxUeoC3hGfh5W3s9FM9uCHDS2SG3LYwBpyTi`
- Alpha Vault: `vaU6kP7iNEGkbmPkLmZfGwiGxd4Mob24QQCie5R9kd2`

### API endpoints

Standard API patterns:

- DLMM API: `https://dlmm-api.meteora.ag/`
- DAMM API: `https://damm-api.meteora.ag/`
- Devnet versions: Replace with `devnet-` prefix

## Frontmatter requirements for pages

- title: Clear, descriptive page title
- description: Concise summary for SEO/navigation
- Additional fields as needed (icon, iconType for cards)

## Writing standards

### Voice and tone

- Second-person voice ("you")
- Professional but accessible
- Action-oriented for guides
- Explain "why" not just "how"

### Structure patterns

For integration guides:

1. Introduction with product context
2. Prerequisites/dependencies
3. Installation steps
4. Code examples with explanations
5. Common configurations
6. Troubleshooting/notes

For concept pages:

1. What is [product]?
2. Key features
3. How it works
4. Use cases
5. Related resources

### Code documentation

- Language tags on all code blocks
- Include imports in examples
- Show both TypeScript and Rust where applicable
- Comment complex operations
- Use realistic values in examples

### Visual elements

- Alt text on all images
- Diagrams for complex flows
- Screenshots for UI references
- CardGroups for related links

### Links and references

- Relative paths for internal links
- Full URLs for external resources
- Link to GitHub repos for SDKs
- Reference API docs where relevant

## Common documentation patterns

### SDK installation

```bash
npm install @meteora-ag/[sdk-name] @solana/web3.js
# or
pnpm install @meteora-ag/[sdk-name] @solana/web3.js
# or
yarn add @meteora-ag/[sdk-name] @solana/web3.js
```

### Feature cards

```mdx
<CardGroup cols={2}>
  <Card title="Feature Name" icon="icon-name" iconType="solid">
    Brief description of the feature and its benefits.
  </Card>
</CardGroup>
```

### Step-by-step guides

```mdx
<Steps>
  <Step title="Action verb + description">
    Detailed explanation of this step.
  </Step>
</Steps>
```

### Important notes

```mdx
<Note>For general important information</Note>

<Warning>For potential issues or gotchas</Warning>

<Info>For supplementary information</Info>
```

## Git workflow

- NEVER use --no-verify when committing
- Ask how to handle uncommitted changes before starting
- Create a new branch when no clear branch exists for changes
- Commit frequently throughout development
- NEVER skip or disable pre-commit hooks

## Do not

- Skip frontmatter on any MDX file
- Use absolute URLs for internal links
- Include untested code examples
- Make assumptions - always ask for clarification
- Create duplicate content without strategic reason
- Use inconsistent terminology
- Mix mainnet and devnet examples without clear labels
- Omit error handling in code examples
- Create overly technical content without context
- Use marketing language in technical documentation
