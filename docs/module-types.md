# Invenio module types

Invenio is a CERN developed framework which mainly uses two languages when it comes to application logics: JavaScript and Python;
and another two when it comes to interface structure and style: HTML and CSS.

The way to create an _Invenio custom module_ will depend on the **language involved for the logic customization**.


## 🐍 Python based customization

This is the most straight-forward case, as the Invenio developers have already created a 🍪 _cookiecutter repository_
to use as reference when creating new Python-based custom modules. Creating on of these modules involve the following steps:

- Create your _custom module_ using the [Invenio module cookiecutter][repo-module-cookiecutter].
- Write your custom modifications, overriding one of the vanilla [Invenio modules][docs-module-reference].
- Add it to the list of project dependencies within your main Invenio-based application.


## ⚛️ JavaScript based customization

The JavaScript case is more complicated, as there is no _official_ reference on how to create these modules. According to
the developers (and a 2021-10-05 response on their `#newcommers-help` Discord channel), users must take the following steps:

- Create your JavaScript _custom module_.
- Add it to the webpack theme list within your main Invenio-based application ([example][repo-example-webpack-list]).
- Add it as a new entry-point within your main Invenio-based application ([example][repo-example-entry-points]).
- Use your custom templates within the main Invenio-based application, if any ([example][repo-example-custom-template]).

Given that there is no _official_ guide on how to structure a JavaScript based custom module, one could take existing
Invenio-based applications as proper references on how to do this. We would recommend checking the [HEPData project][repo-hepdata],
and how they created their own JavaScript custom module for:

- The [search visualization][repo-hepdata-search-module].
- The [application theme][repo-hepdata-theme-module].


[docs-module-reference]: https://invenio.readthedocs.io/en/latest/documentation/bundles/index.html
[repo-example-webpack-list]: https://github.com/inveniosoftware/invenio-app-rdm/blob/v6.0.4/invenio_app_rdm/theme/webpack.py
[repo-example-entry-points]: https://github.com/inveniosoftware/invenio-app-rdm/blob/v6.0.4/setup.py#L102
[repo-example-custom-template]: https://github.com/inveniosoftware/invenio-app-rdm/blob/v6.0.4/invenio_app_rdm/records_ui/templates/semantic-ui/invenio_app_rdm/records/deposit.html
[repo-hepdata]: https://github.com/HEPData/hepdata
[repo-hepdata-search-module]: https://github.com/HEPData/hepdata/tree/master/hepdata/modules/search
[repo-hepdata-theme-module]: https://github.com/HEPData/hepdata/tree/master/hepdata/modules/theme
[repo-module-cookiecutter]: https://github.com/inveniosoftware/cookiecutter-invenio-module
