# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Architecture

**Semantic Flow** is a framework for managing and publishing knowledge graphs and semantic data using GitHub/GitLab and static hosting. The workspace contains multiple interconnected components:

### Main Components

- **sf-api/**: API component (currently empty structure)
- **sf-cli/**: Command-line application that consumes the sf-api
- **sf-service/**: Service component (currently empty structure)  
- **sf-ontology/**: Ontology definitions (currently empty)
- **sflow-dendron-notes/**: Complete documentation and specification in Dendron format
- **test-ns/**: Test namespace

### Documentation Structure

All project documentation, specifications, and design decisions are stored in `sflow-dendron-notes/` using Dendron's hierarchical note system. Key documentation includes:

- **Core concepts**: `sflow.concepts.*` files define the semantic mesh architecture
- **Product specifications**: `sflow.products.*` files detail each component
- **Requirements**: `sflow.requirements.md`
- **Use cases**: `sflow.use-cases.*` files
- **Conversation logs**: `sflow.conv.*` files track design decisions and development history; BEWARE! These conversations contain information and decisions that have been superceded. 

### Dendron Workspace

This is a Dendron workspace configured in `dendron.yml` with:
- Knowledge base in `sflow-dendron-notes/` vault
- Git integration with remote repository
- Publishing enabled to `docs/` folder
- Task management, journaling, and scratch note features

## Key Concepts

**Semantic Mesh**: A dereferenceable, versioned collection of semantic data where every HTTP IRI returns meaningful content.

**Core Elements**:
- **Datasets**: Bundles of data with optional immutable, versioned history
- **Namespaces**: URL-based hierarchical organization
- **Identifiers**: Persistent URLs for namespaces, datasets, and other entities

**Workflow**: Creation → Editing → Weaving → Publishing using GitHub Pages and SSG (Static Site Generator)

## Development Guidelines

### Working with Documentation

- All specifications and design decisions are in `sflow-dendron-notes/`
- Use Dendron's hierarchical naming: `sflow.concepts.mesh.md`, `sflow.products.sf-cli.md`
- Reference related concepts using Dendron's wiki links: `[[sflow.concepts.dataset]]`

### Component Development

- Each component (sf-api, sf-cli, sf-service) should follow the architecture defined in the documentation
- Refer to `sflow.products.*` files for component specifications
- Check conversation logs in `sflow.conv.*` for context on design decisions

### Versioning and Git

- Source content lives in `src/` folders within components
- Generated/published content goes to `docs/` folders
- Immutable versioning system creates `v*` versions for changed datasets
- Git commits track both source changes and successful generation

### RDF and Semantic Web

- Supports multiple RDF formats (.trig, .jsonld, etc.)
- Uses DCAT for dataset catalogs
- Implements schema:sameAs for aliasing
- Maintains backwards compatibility for all published IRIs