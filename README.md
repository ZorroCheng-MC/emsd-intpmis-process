# EMSD INTPMIS Process Repository

This repository handles document processing workflows for the EMSD Integrated Project Management Information System (INTPMIS).

## Repository Structure

```
emsd-intpmis-process/
├── docs/                          # Documentation
│   ├── setup/                     # Setup guides
│   ├── workflows/                 # Workflow documentation
│   └── api/                       # API documentation
├── source/                        # Source documents for processing
│   ├── templates/                 # Document templates
│   │   ├── project_docs/          # Project documentation templates
│   │   ├── system_specs/          # System specification templates
│   │   └── operations/            # Operations manual templates
│   ├── references/                # Reference documents
│   │   ├── standards/             # Government standards and guidelines
│   │   ├── samples/               # Sample documents from other projects
│   │   └── specifications/        # Technical specifications
│   └── schemas/                   # Database and data schemas
├── workflows/                     # GitHub Actions workflows
│   ├── document_processing.yml    # Main document processing workflow
│   ├── quality_check.yml         # Document quality validation
│   └── deployment.yml            # Deployment workflow
├── scripts/                       # Processing scripts
│   ├── converters/               # Document format converters
│   ├── validators/               # Document validators
│   └── generators/               # Content generators
├── generated/                     # Generated/processed documents
│   ├── drafts/                   # Draft documents
│   ├── reviewed/                 # Reviewed documents
│   └── approved/                 # Approved final documents
├── config/                       # Configuration files
│   ├── processing_rules.json    # Document processing rules
│   ├── validation_schemas.json  # Validation schemas
│   └── templates_config.json    # Template configurations
└── tests/                        # Test files
    ├── unit/                     # Unit tests
    ├── integration/              # Integration tests
    └── fixtures/                 # Test fixtures
```

## Purpose

This repository manages the document generation and processing pipeline for EMSD INTPMIS project documentation.
