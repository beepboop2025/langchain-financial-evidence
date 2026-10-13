# Publishing

This package is maintained in `beepboop2025/langchain-financial-evidence`.
Its initial source was extracted from the MIT-licensed Financial Evidence
integration after review. This repository has its own version and release tags.

CI tests offline native-tool behavior on Python 3.10, 3.12 and 3.13, including
LangChain Core 1.6.6 and 1.6.9. All workflow actions are pinned to commit SHAs.
Live API tests are opt-in and do not run automatically.

## PyPI trusted publisher

Version 0.1.0 was published through the following PyPI trusted publisher.
Verify that this existing configuration remains valid before another release;
the workflow does not configure or replace it. No API token is stored here.

| Field | Value |
| --- | --- |
| PyPI project | `langchain-financial-evidence` |
| Owner | `beepboop2025` |
| Repository | `langchain-financial-evidence` |
| Workflow filename | `publish.yml` |
| Environment | `pypi` |

Create and review a version tag such as `v0.1.1`, ensuring the tag's
`pyproject.toml` version matches. GitHub release assets and PyPI publication are
separate actions. Run **Publish to PyPI** from the `main` branch with version
`0.1.1`. It checks out that version tag, tests and builds the package, then uses
GitHub OIDC in the `pypi` environment to publish. A dispatch is an explicit
publication action; it is not a readiness probe. The workflow does not create
accounts, tokens, projects or trust relationships on PyPI.

Before dispatch, confirm the new version is unused on PyPI, merge the tested
commit through review, verify its exact identity on `main`, and create the tag
at that reviewed commit. The workflow checks package identity and version but
does not enforce tag ancestry, so this source-identity preflight is required.
Retain wheel and source-archive hashes. After publication, compare the public
PyPI distributions with the workflow artifacts, install the exact wheel in a
fresh environment, and verify a central hosted request. Label live verification
as synthetic traffic; retain only routing/status/schema evidence, not responses.

After publication, independently install the exact package version from PyPI
and verify a bounded tool invocation. Only then submit the
[LangChain integration listing form](https://github.com/langchain-ai/docs/issues/new?template=06-integration-submission.yml).
Catalog acceptance remains subject to LangChain maintainer review. Do not
request a hosted guide or featured status without meeting their requirements.
