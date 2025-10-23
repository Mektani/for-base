# for-base

#!/usr/bin/env bash
# .git/hooks/pre-commit
# Simple pre-commit: run tests and lint, stop commit on failure

echo "Running pre-commit checks…"

# 1) run tests (change to your test command)
npm test
RESULT_TESTS=$?

# 2) run linter (change or remove if not needed)
npm run lint
RESULT_LINT=$?

if [ $RESULT_TESTS -ne 0 ] || [ $RESULT_LINT -ne 0 ]; then
  echo "Pre-commit checks failed. Fix issues before committing."
  exit 1
fi

echo "All checks passed — you can commit."
exit 0
