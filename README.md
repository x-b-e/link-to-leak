This reproduces a "bug" (or at least a difference in handling) between FastBoot-rendered markup and non-FastBoot-rendered markup when `LinkTo` components are nested. This is new behavior, but I didn't isolate exactly which version of Ember it appeared in.

TL;DR The nested link to is rendered outside of its parent in FastBoot, but not when FastBoot is disabled.

```
<LinkTo @route="application" style="font-weight: bold;">
  <LinkTo @route="application">
    I should be bold because I should be nested in the other anchor.
  </LinkTo>
</LinkTo>
```

Yes, yes... [nested anchor tags](https://www.w3.org/TR/html401/struct/links.html#h-12.2.2) are illegal, and so maybe this isn't a bug, but the difference is unexpected, and so maybe it is.
