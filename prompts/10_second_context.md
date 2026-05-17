# 10 Second Context

You are working with the Promethink Dev display repo.

Use it to prepare read-models for UI, not runtime behavior.

## What matters

- project sprint data must come from an explicit sprint source;
- `governance.snapshot` is for product health and status only;
- step stream is separate from sprint metadata;
- project sprint list is structured data, not a chat reply;
- missing source must render as empty state;
- trace should stay compact, readable, and collapsible.

## Do not mix

- agent governance batch history
- target project sprint list
- raw private reasoning
- shell layout changes

## Expected output shape

- sprint cards
- task cards
- source label
- readable step summaries
- optional trace disclosure
- empty state when no source exists
