# Rackspace Cloud DNS and Managed DNS API documentation

[![Netlify Status](https://api.netlify.com/api/v1/badges/03478696-b59d-4713-af76-268491e05cf6/deploy-status)](https://app.netlify.com/sites/docs-cloud-cdn/deploys)

This repository contains the source files that generate the following Cloud DNS and Managed
DNS API documentation:

* [Cloud DNS Quickstart Guide](https://developer.rackspace.com/docs/cloud-dns/v1/developer-guide/#document-quickstart-guide)
* [Cloud DNS Developer Guide](https://developer.rackspace.com/docs/cloud-dns/v2/developer-guide/#document-developer-guide)
* [CLOUD DNS API Reference](https://developer.rackspace.com/docs/cloud-dns/v2/developer-guide/#api-reference)

* [Managed DNS Quickstart Guide](https://developer.rackspace.com/docs/cloud-dns/v2/developer-guide/#document-quickstart-guide)
* [Managed DNS Developer Guide](https://developer.rackspace.com/docs/cloud-dns/v2/developer-guide/#document-developer-guide)
* [Managed DNS API Reference](https://developer.rackspace.com/docs/cloud-dns/v2/developer-guide/#api-reference)

When you commit changes to the master branch of this repository, the
Strider CI/CD build job builds the documentation. Successful builds are deployed to production.

<!-- When you commit changes to the master branch of this repository, the 
[Strider CI/CD build job](https://build.developer.rackspace.com/rackerlabs/docs-cloud-dns/)
builds the documentation. Successful builds are deployed to production. -->

## Local Setup

`npm i -g netlify-cli`
`netlify init`
`netlify build`
`netlify dev`
`netlify deploy`

### Support and feedback

We welcome feedback, comments, and bug reports. Follow the [contributor guidelines](CONTRIBUTING.md)
to propose a source file change, or [submit a GitHub issue](https://github.com/rackerlabs/docs-cloud-dns/issues/new)
to request an update or to provide feedback.

You can also contact the [Rackspace documentation team](mailto:devdoc@rackspace.com) directly for general
issues or questions about the content.
