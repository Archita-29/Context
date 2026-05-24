# Memact

Memact is a user-controlled context layer for app personalization.

Apps send context. App categories give it shape. Wiki gives users control.

## Current core

- Access handles consent, apps, API keys, scopes, and permissions.
- Wiki is the user-facing context layer where users add, edit, approve, reject, delete, and share context.
- Schema defines app category schemas.
- Memory stores accepted context, history, retrieval, and app-safe summaries.
- Contracts define shared shapes.
- SDK lets apps connect to Memact.

## Open-source contribution model

Memact open-source contributors mainly work on app category schemas.

Contributors do not build random generic features. Pick an app category and define how context should work there.

Examples: music, video-streaming, movie-booking, shopping, learning, news-articles, fitness, travel, food-delivery, creator-tools, productivity, and AI assistants.

For each category, contributors can add:

- category schema
- useful context fields
- example app context dumps
- normalization rules
- user-facing Wiki entry templates
- user prompts for missing context
- access suggestions
- tests

## Contributor assignments

1. Category schema contributor: pick an app category and define what user context matters.
2. Context example contributor: add realistic messy app context examples and expected Wiki outputs.
3. Normalization contributor: write simple rules that convert messy app context into clean Wiki entries.
4. User prompt contributor: write prompts that help users add missing context.
5. Entry template contributor: write clean Wiki entry templates for category context.
6. Access suggestion contributor: suggest what permissions apps in a category should request.
7. Test contributor: add test cases for schemas, normalization, privacy, and public/private behavior.

## Rules

- Default visibility should be private.
- Apps should not get full Wiki access.
- Apps should only get relevant category context with permission.
- User-added context is stronger than app-proposed context.
- Important app writes should require approval.
- Do not infer sensitive traits.
- Do not write fake certainty.
- Keep user-facing copy simple.
- Do not bring back Capture, Inference, or Intent as core product language.

## Best short explanation

Apps send context. App categories give it shape. Wiki gives users control.
