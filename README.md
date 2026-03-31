# Turborepo watch mode with dependencies

## Problem

When using `turbo watch <task>`, changes to dependencies are not detected if the dependent package does not have a
`<task>` defined, even though the task is included in the task graph. This goes against the turbo documentation, which 
states that `turbo watch` respects the task graph.

## Steps to Reproduce

1. Run `pnpm install`
2. Run `turbo watch dev`
3. Observe that a change in apps/app-a/src/index.js triggers a rebuild of `app-a`
4. Observe that a change in packages/package-a/src/index.js **does not** trigger rebuild of `package-a`

## Expected Behavior

When making a change in packages/package-a/src/index.js, `turbo watch dev` should see the change and rebuild `package-a`