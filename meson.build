project(
	'mcwayface',
	'c',
	version: '0.0.1',
	license: 'MIT',
	meson_version: '>=0.43.0',
	default_options: [
		'c_std=c11',
		'warning_level=2',
		'werror=false',
	],
)

add_project_arguments(['-Wno-unused-parameter', '-DWLR_USE_UNSTABLE'], language: 'c')

cc = meson.get_compiler('c')
# Clang complains about some zeroed initializer lists (= {0}), even though they
# are valid
if cc.get_id() == 'clang'
	add_project_arguments('-Wno-missing-field-initializers', language: 'c')
	add_project_arguments('-Wno-missing-braces', language: 'c')
endif

# Avoid wl_buffer deprecation warnings
add_project_arguments('-DWL_HIDE_DEPRECATED', language: 'c')

pixman         = dependency('pixman-1')
wlroots        = dependency('wlroots')
wayland_server = dependency('wayland-server')

executable(
	'mcwayface',
	[
		'src/main.c'
	],
	dependencies: [
		pixman,
		wlroots,
		wayland_server,
	]
)
