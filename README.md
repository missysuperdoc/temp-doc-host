# Document API Test Outputs

This repo holds the review artifacts for SuperDoc Document API command testing.

## What is in this repo

- `Reports/Command Support.xlsx`
  - the main spreadsheet that tracks commands, expected behavior, XML notes, manual review, and Linear tickets
- `Output/`
  - output `.docx` files created by the command test runs
- `Starting files/`
  - base `.docx` files used to run the tests

## Main file to review

- [Reports/Command Support.xlsx](./Reports/Command%20Support.xlsx)

## Output files to review

- [Output/](./Output/)

## What the spreadsheet means

Each row is one Document API command.

Important columns:

- `Method`
  - the command name
- `Layperson description`
  - what the command is supposed to do and what the output document should look like
- `Output file`
  - the generated `.docx` file for that command
- `Manual Testing PASS/FAIL`
  - human visual review result
- `XML Codex Test`
  - machine review result
- `Linear ticket`
  - linked bug ticket if there is a known problem

## How the artifacts are generated

The actual runner lives in the sibling `superdoc` repo.

Expected folder layout:

```text
parent-folder/
  superdoc/
  temp-doc-host/
```

Run from inside the `superdoc` repo:

```bash
./scripts/docapi-command-suite/run-docapi-suite.sh
```

That command:

1. discovers newly added commands
2. runs real tests only for commands that are not already in the spreadsheet
3. writes output `.docx` files into this repo
4. updates the spreadsheet in this repo
5. merges manual review and Linear data
6. pushes the updated spreadsheet here

## Notes

- The daily run is intentionally incremental.
- It does not rerun every command every time.
- It only runs tests for commands that are new to the spreadsheet.
