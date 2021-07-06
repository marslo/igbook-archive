# simple-theme

**Table of Contents** _generated with_ [_DocToc_](https://github.com/thlorenz/doctoc)

* [Q&A](simple-theme.md#qa)
  * [workaround for in-progress image float layer out](simple-theme.md#workaround-for-in-progress-image-float-layer-out)
  * [`page-header` background color](simple-theme.md#page-header-background-color)

## Q&A

### [workaround for in-progress image float layer out](https://github.com/afonsof/jenkins-material-theme/issues/183#issuecomment-806518351)

```css
svg[class*=anime] { visibility: collapse }
```

### `page-header` background color

```css
a.page-header__brand-link {
  background: #43a047 !important;
  color: white !important;
  font-size: large !important;
}
.page-header__brand-image {
    height: 3rem !important;
    width: 3rem !important;
}
```

