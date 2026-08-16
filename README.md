# Odoo DevKit

Odoo DevKit adds Odoo-aware completion, navigation, and type checking to PyCharm, across Python,
XML views, QWeb/Owl templates, JavaScript, and SQL. Suggestions are scoped to your addon's Odoo
version and `depends` list, not just the file you're editing.

This repository is the public home for Odoo DevKit. Use it to check what the plugin does, report
bugs, and request features. It does not contain the plugin's source.

## Why

Odoo resolves models, fields, and dependencies at runtime, spread across Python, XML, templates,
and SQL. A generic Python type checker only ever sees one class at a time, so it can't reconstruct
any of that on its own. Odoo DevKit reads your Odoo source, manifests, and addons directly, instead
of guessing from a list of snippets.

## Features

- **Models, fields, and types** — completion and Go to Declaration for models and fields
  everywhere they appear: `_name`, `_inherit`, `_inherits`, relational fields, `related=`,
  `_order`, `vals` dicts, `env[...]`, and XML `model=`/`ref=`. Go to Declaration also covers
  methods, magic fields, `super()` calls, and Selection values, with hover documentation on field
  declarations. Recordset typing for `self`, `env[...]`, relational chains, ORM calls like
  `sudo()` and `filtered()`, and typed test helpers such as `Form`. Selection value validation,
  including `selection_add` across modules, and a warning the moment a model falls outside your
  addon's `depends` list.
- **QWeb and Owl templates** — HTML completion inside `<templates>`, plus every `t-*` directive
  matched to where you're using it. Python completion inside `eval=`, `context=`, `domain=`, view
  modifiers, server actions, and `mail.template`, each with the right variables. A built-in
  language for Owl's `t-*` expressions, with completion and navigation straight into your JS
  components. XPath 1.0 evaluation for resolving inherited views and navigating from
  `<xpath expr=>` to the matched node. CSS completion and navigation for `class=` and `id=` inside
  templates (PyCharm Professional).
- **JavaScript and Owl components** — completion and navigation for `registry.category(...)` and
  `useService(...)`. ES modules (`@addon/path`) and legacy `odoo.define`/`require` modules resolve
  to the same file. Owl component tag and prop completion, navigating both directions between
  JavaScript components and XML templates. Typed `this.state`, `this.props`, and injected
  services.
- **SQL support** (PyCharm Professional) — PostgreSQL syntax highlighting inside `cr.execute(...)`
  and SQL constraints. Table and column completion based on Odoo models and fields. Go to
  Declaration from a SQL string straight to the Python field.
- **Inspections and refactoring** — warnings for unresolved models, fields, and Selection values,
  scoped to your addon's dependencies. Warnings for outdated syntax (`<tree>`→`<list>`,
  `attrs=`/`states=` removed, `t-esc`→`t-out`), matched to your Odoo version. Find Usages and
  Rename that understand Odoo model names, not just Python class names.

## Requirements

- PyCharm Community or Professional, 2026.2 or newer (build 262+).
- SQL and CSS features need PyCharm Professional, with the matching bundled plugin enabled.
- JavaScript and Owl support works in both editions, limited by PyCharm Community's own, more
  restricted JavaScript support.
- Supports Odoo 10+, with version-aware analysis based on your project's Odoo source and
  manifests.

## Getting the plugin

Odoo DevKit is distributed through JetBrains Marketplace. In PyCharm, go to
**Settings → Plugins → Marketplace** and search for "Odoo DevKit", or install it from the
Marketplace listing directly. A 30-day trial is available before you need to activate a license.

## Reporting bugs and requesting features

Open an [issue](../../issues) in this repository. Include your PyCharm version, Odoo version, and
a minimal reproduction if you can. For anything else, email
[odonexussoft@gmail.com](mailto:odonexussoft@gmail.com).

## License

Odoo DevKit is a commercial plugin. Pricing, license terms, and trial details are on the
JetBrains Marketplace listing.
