# Shared JetBrains Runtime Setup

This is a helper to use JetBrains Runtime with GitHub Actions.

```yaml
jobs:
  build:
    name: Building with JetBrains Runtime
    runs-on: linux-latest
    steps:
      # checkout your own repository first, 
      #  then add the following steps before steps using Java 

      - name: Checkout JetBrains Setup
        uses: actions/checkout@v4
        with:
          repository: jansorg/github-actions-jbr-setup
          path: .github/shared_actions/jbr

      - name: Install JetBrains Runtime
        uses: ./.github/shared_actions/jbr/setup_jbr17

      - name: Verify Java Setup
        shell: bash
        run: |
          java --version
          which java
```