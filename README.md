## `go mod why -m` output:

```
$ go mod why -m github.com/docker/docker
# github.com/docker/docker
(main module does not need module github.com/docker/docker)
```

## trivy scan output

```
$ trivy fs .
2024-10-22T21:19:21-07:00       INFO    [vulndb] Need to update DB
2024-10-22T21:19:21-07:00       INFO    [vulndb] Downloading vulnerability DB...
2024-10-22T21:19:21-07:00       INFO    [vulndb] Downloading artifact...        repo="ghcr.io/aquasecurity/trivy-db:2"
54.61 MiB / 54.61 MiB [-------------------------------------------------------------------------------------------------------------] 100.00% 6.74 MiB p/s 8.3s
2024-10-22T21:19:30-07:00       INFO    [vulndb] Artifact successfully downloaded       repo="ghcr.io/aquasecurity/trivy-db:2"
2024-10-22T21:19:30-07:00       INFO    [vuln] Vulnerability scanning is enabled
2024-10-22T21:19:30-07:00       INFO    [secret] Secret scanning is enabled
2024-10-22T21:19:30-07:00       INFO    [secret] If your scanning is slow, please try '--scanners vuln' to disable secret scanning
2024-10-22T21:19:30-07:00       INFO    [secret] Please see also https://aquasecurity.github.io/trivy/v0.56/docs/scanner/secret#recommendation for faster secret detection
2024-10-22T21:19:30-07:00       INFO    Number of language-specific files       num=1
2024-10-22T21:19:30-07:00       INFO    [gomod] Detecting vulnerabilities...
```

## govulncheck output

```
$ govulncheck .
=== Symbol Results ===

No vulnerabilities found.

Your code is affected by 0 vulnerabilities.
This scan also found 0 vulnerabilities in packages you import and 3
vulnerabilities in modules you require, but your code doesn't appear to call
these vulnerabilities.
Use '-show verbose' for more details.
```

## component detection output

See [ScanManifest_20241022211025173.json](./ScanManifest_20241022211025173.json)

```
$ grep github.com/docker/docker ScanManifest_20241022211025173.json
          "github.com/docker/docker v26.0.1+incompatible - Go",
        "github.com/docker/docker v26.0.1+incompatible - Go": null,
        "name": "github.com/docker/docker",
          "Name": "github.com/docker/docker",
        "id": "github.com/docker/docker v26.0.1+incompatible - Go"
```
