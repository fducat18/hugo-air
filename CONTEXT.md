# Hugo Air Theme Context

This context defines language for the public hugo-air theme and its relationship to downstream Hugo sites.

## Language

**Theme Consumer**:
A Hugo site repository that uses this theme as a dependency.
_Avoid_: tenant, client app

**Theme Core**:
Template, shortcode, and style files maintained in this repository for shared reuse.
_Avoid_: consumer customization layer

**Customization Surface**:
Supported ways a Theme Consumer adapts behavior through configuration, content, and Hugo override mechanisms.
_Avoid_: direct core patching

**Compatibility Promise**:
Expectation that changes in Theme Core preserve consumer workflows unless a documented breaking change is intentional.
_Avoid_: best effort only

**Reusable Improvement**:
A bug fix or feature implemented in Theme Core because multiple Theme Consumers can benefit.
_Avoid_: one-off site patch

**Upstream Contribution**:
A proposed change from maintainers or community contributors to improve Theme Core.
_Avoid_: private hotfix branch

**Ownership Migration**:
Systematic update of repository owner references and public URLs after account transfer.
_Avoid_: partial URL replacement

## Example dialogue

Consumer dev: "I need a new layout variant for listing pages."
Theme maintainer: "First try Customization Surface. If that cannot express it, propose a Reusable Improvement."
Consumer dev: "If accepted, we get it through normal update?"
Theme maintainer: "Yes, via Upstream Contribution merged into Theme Core under Compatibility Promise."
