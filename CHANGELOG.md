Changelog
=========

### 0.5.0 (14/12/2014)

- Renamed `django_react.exceptions.PropSerialisationError` to `django_react.exceptions.PropSerializationError`.
- Rolled the bundling functionality out into a more easily overridable interface. You can now define a `bundle` attribute on `ReactComponent` inheritors which should be an extended `django_webpack.models.WebpackBundle`.
- Renamed the following attributes on `ReactComponent`:
  - `entry` is now `source`
  - `library` is now `variable`
- Renamed the `get_library` method on `ReactComponent` to `get_variable`
- Removed the following methods on `ReactComponent`:
  - `get_serialised_props_hash`
  - `get_component_id`
  - `get_react_variable`
  - `get_component_name`
  - `has_props`
- The render_* methods now use standard Django templates where possible.
- Removed the `render_to_string` and `render_to_static_markup` methods from `django_react.react`. In their place, use `django_react.react.render`.
- The react external can now be configured on a per-bundle basis, or globally by using the `DJANGO_REACT['REACT_EXTERNAL']` setting.
- Updated django-node and django-webpack dependencies to the latest.
- Added a test suite and harness.
- Added basic documentation.

### 0.4.0 (11/12/2014)

- Fixed a bug where errors caused during a component's prop serialization could silently fail.
- Excised the bundling tooling into a standalone app, `django_webpack`
- Renamed `SerialisationException` to `PropSerializationError`.
- Renamed `RenderException` to `RenderingError`.
- Renamed the `django_react.utils` module to `django_react.react`.
- `ReactComponent.render` is now `ReactComponent.render_to_string`
- `ReactComponent.render_static` is now `ReactComponent.render_to_static_markup`
- `ReactComponent.get_component_variable` is now `ReactComponent.get_library`.
- Moved the Webpack configuration into the ReactComponent class.

### 0.3.0 (3/12/2014)

- `django_react.exceptions.ReactComponentSourceFileNotFound` is now `django_react.exceptions.SourceFileNotFound`
- `django_react.exceptions.ReactComponentRenderToStringException` is now `django_react.exceptions.RenderException`
- `django_react.exceptions.ReactComponentBundleException` is now `django_react.exceptions.BundleException`
- `django_react.models.ReactComponent` now has additional methods: `generate_path_to_bundled_source`, `write_bundled_source_file`, `generate_bundled_source_file`, `get_rel_path_to_bundled_source`, and `get_url_to_bundled_source`.
- `django_react.utils.bundle` no longer accepts a `ReactComponent` as an argument, it now takes `entry` and `library`.
- `django_react.utils.render` no longer accepts a `ReactComponent` as an argument, it now takes `path_to_source`, `serialised_props`, and `to_static_markup`.
- `django_react/render.js` no longer accepts the `--path-to-component` argument, instead it takes `--path-to-source`.

### 0.2.0 (3/12/2014)

- Replaced the post-install step in setup.py with django-node's dependency and package resolver.

### 0.1.0 (2/12/2014)

- Initial release