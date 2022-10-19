# Contributing to cxl-tool

Thank you for taking the time to contribute to cxl-tool.

The following is a set of guidelines that we adhere to, and request that
contributors follow.

1. The cxl developers primarily use
   the [nvdimm](https://subspace.kernel.org/lists.linux.dev.html)
   mailing list for everything. It is recommended to send patches to
   **```nvdimm@lists.linux.dev```**
   An archive is available on [lore](https://lore.kernel.org/nvdimm/)

1. Github [issues](https://github.com/computexpresslink/cxl-tool/issues)
are an acceptable way to report a problem, but if you just have a question,
   [email](mailto:nvdimm@lists.linux.dev) the above list.

1. We follow the Linux Kernel [Coding Style Guide][cs] as applicable.

   [cs]: https://www.kernel.org/doc/html/latest/process/coding-style.html

1. We follow the Linux Kernel [Submitting Patches Guide][sp] as applicable.

   [sp]: https://www.kernel.org/doc/html/latest/process/submitting-patches.html

1. We follow the Linux Kernel [DCO][dco] (Developer Certificate of Origin).
   The DCO is an attestation attached to every contribution made by every
   developer. In the commit message of the contribution, the developer simply
   adds a Signed-off-by statement and thereby agrees to the DCO.

   [dco]: https://developercertificate.org/

1. Github Pull Requests are acceptable mainly for smaller, more obvious fixups,
   but won't be merged directly, as Github doesn't allow for the kernel style
   flow of patches where a maintainer also signs off on the patches they apply.
   Larger changes may need to be sent to the mailing list so that everyone gets
   an opportunity to review them.

1. **Misc Best Practices:**
   1. Use a subject prefix of "cxl PATCH" (or "cxl PATCH vN" for a new
      revision). This can be automated for a ```git format-patch``` command
      by setting a repo-local git config setting:
         ```git config format.subjectprefix "cxl PATCH"```

   1. For commit messages: Describe the change and why it was needed. Use a
      concise subject line, and a blank line between the subject and the body,
      as well as between paragraphs. Use present tense and the imperative mood
      (e.g. "Add support for.." instead of "Added support.." or "Adding
      support"). Word-wrap to 72 columns.
