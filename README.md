# @mostlyserious/formatters

✨ Formatters made to work with std in/out (useful for IDEs) and some helpful additional config.

## Overview

This package provides stdin/stdout wrappers for popular code formatters, making them easy to integrate with IDEs and text editors. Each formatter is designed to read from stdin and output to stdout, enabling seamless integration with editor formatting workflows.

## Installation

```bash
bun add @mostlyserious/formatters --global
```

## Available Formatters

### std-pint
PHP code formatter using Laravel Pint.

**Usage:**
```bash
echo "<?php echo 'hello world';" | std-pint
```

**Features:**
- Auto-installs Laravel Pint via Composer if not present
- Processes PHP code from stdin
- Returns formatted code to stdout
- Supports all Pint command-line options

### std-rustywind
Tailwind CSS class sorter using rustywind.

**Usage:**
```bash
# Default HTML/JSX processing
echo '<div class="p-4 bg-red-500 text-white">' | std-rustywind

# CSS processing (for @apply directives)
echo '@apply p-4 bg-red-500 text-white;' | std-rustywind css

# JavaScript processing
echo "el.setAttribute('class', 'p-4 bg-red-500 text-white')" | std-rustywind js

# Svelte processing
echo '<div class="p-4 bg-red-500 text-white"></div><style> .selector { @apply p-4 bg-red-500 text-white; } </style>' | std-rustywind svelte
```

**Features:**
- Auto-installs rustywind via Homebrew if not present
- Supports multiple file types with custom regex patterns
- Handles CSS `@apply` directives, JavaScript class attributes, and Svelte components

### std-stylelint
CSS/SCSS linter and formatter using Stylelint.

**Usage:**
```bash
# Standard CSS/SCSS
echo 'body { color: red; }' | std-stylelint

# HTML with embedded CSS
echo '<style>body { color: red; }</style>' | std-stylelint html
```

**Features:**
- Auto-installs Stylelint and postcss-html via Bun if not present
- Auto-generates `stylelint.config.js` with sensible defaults if missing
- Supports HTML processing with embedded CSS
- Automatically fixes formatting issues

## IDE Integration

These formatters are designed to work seamlessly with IDE formatting features:

1. Configure your IDE to use the appropriate `std-*` command as a formatter
2. Set the formatter to read from stdin and write to stdout
3. The formatter will handle dependency installation automatically
