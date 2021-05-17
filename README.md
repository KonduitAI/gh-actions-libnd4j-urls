# gh-actions-libnd4j-urls
This is a repository for dynamically updated libnd4j urls to work around github actions slow builds.
This should only be used as a last resort.
An example github action step that uses this repo is:
https://github.com/eclipse/deeplearning4j/blob/e646df702657262b47e2aaefd677912cde1f7202/.github/workflows/build-deploy-linux-cuda-11.0.yml#L92

The associated bootstrap script that uses the urls in this repo can be found [here](https://github.com/eclipse/deeplearning4j/blob/e646df702657262b47e2aaefd677912cde1f7202/bootstrap-libnd4j-from-url.sh)

An individual file in this repo will be used relative to the matrix state:
1. os
2. libnd4j helper: (The optional accelerator for convolution operations such as cudnn, onednn, armcompute)
3. The extension: avx2,avx412

A url will be updated for use with that particular state of a matrix. This should be used only in a manual workflows.

The ideal workflow for releases is as follows:

1. Build libnd4j for release
2. Download that tag
3. Upload to a public url for consumption by the build
4. Update the associated file for the matrix configuration with ONLY the url and nothing else
for that download.
5. Invoke the build specifying 1 for invoking a libnd4j download.
