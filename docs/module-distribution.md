# Invenio modules distribution

Invenio is a framework based on modules, small software components that add functionality to a small part of the whole web application.
They are added to the main application by using something similar to a _plug-in_ system. Most them are already provided by the Invenio team,
usually bundled in _"packs"_ that fulfill very specific system responsibilities (_authentication_, _files_, _metadata_...), as seen in their
[module reference webpage][docs-module-reference].


## Module hosting

The Invenio provided modules are hosted within the `inveniosoftware` [GitHub organization][org-github-invenio].
They are open-source so that every developer can see how their logic works, and how are their contents structured.
However, when it comes to distribution, the Invenio team _builds_ the corresponding _packages_ / _libraries_
out of those repositories, and uploads them to a _package registry_ such as:

- [PyPi][org-pypi-invenio] for their Python packages.
- [NPM][org-npm-invenio] for their JavaScript packages.


## Module distribution

Developers can rely on these package registries, or install their modules directly from GitHub, if they do not plan to distribute them
outside their organization. In any of these cases they would need to rely on a CLI utility that simplifies the _package fetching_ operation.
Some good _package fetching_ CLI tool examples are:

- [pip][docs-tool-pip] for Python packages.
- [npm][docs-tool-npm] for JavaScript packages.

What changes across _distribution types_ is how the syntax for these CLI tools to fetch packages varies:

### 🏗️ Registry platforms
When having the packages uploaded to a _package registry_, the fetching syntax would be very straight-forward,
as it would only contain their names and versions.

Python `setup.py` example:
```python
setup(
    # ...
    install_requires=[
        # ...
        "invenio-accounts==1.4.7",
    ],
)
```

JavaScript `packages.json` example:
```json
{
  "dependencies": {
    "invenio-search-js": "^1.5.4"
  }
}
```

### 🐙 Git platforms
When only having the packages hosted on a GIT platform (such as GitHub or GitLab), the fetching syntax would need to be changed
to reflect the precise URL where that package is made available.

Python `setup.py` example:
```python
setup(
    # ...
    install_requires=[
        # ...
        "invenio-accounts @ git+https://github.com/inveniosoftware/invenio-accounts@v1.4.7#egg=invenio-accounts",
    ],
)
```

JavaScript `packages.json` example:
```json
{
  "dependencies": {
    "invenio-search-js": "git+https://github.com/inveniosoftware/invenio-search-js.git#v1.5.4"
  }
}
```



[docs-module-reference]: https://invenio.readthedocs.io/en/latest/documentation/bundles/index.html
[docs-tool-npm]: https://docs.npmjs.com/cli/v7
[docs-tool-pip]: https://pip.pypa.io/en/stable/
[org-github-invenio]: https://github.com/inveniosoftware
[org-npm-invenio]: https://www.npmjs.com/~invenio
[org-pypi-invenio]: https://pypi.org/user/inveniosoftware/
