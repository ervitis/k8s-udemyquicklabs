# Notes

## Creating operator

Using `operator-sdk` with version `v1.4.0-13`

First, init

```bash
operator-sdk init --domain nazonazo.dev --plugins helm
```

Then, create the api scaffold

```bash
operator-sdk create api --group nazo --version v1 --kind VisitorsApp
```