# config

**Table of Contents** _generated with_ [_DocToc_](https://github.com/thlorenz/doctoc)

* [Mailing format](./#mailing-format)

## Mailing format

* Show the logs after building
  * Format:

    ```text
    ${BUILD_LOG, maxLines, escapeHtml}
      maxLines: 250
    ```

  * For example:

    ```text
    ${BUILD_LOG, maxLines=8000, escapeHtml=true}
    ```

