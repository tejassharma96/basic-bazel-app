platform :ios, '14.0'

use_frameworks!
inhibit_all_warnings!

source 'git@gitlab.zgtools.net:zillow/ios/libraries/PodSpecs.git'
source 'https://cdn.cocoapods.org/'

use_frameworks!

install! 'cocoapods',
         integrate_targets: false

target 'App' do
	pod 'SDWebImage'
end

plugin 'cocoapods-bazel', {
  rules: {
    'apple_framework' => { load: '@build_bazel_rules_ios//rules:framework.bzl', rule: 'apple_framework' }.freeze,
    'ios_application' => { load: '@build_bazel_rules_ios//rules:app.bzl', rule: 'ios_application' }.freeze,
    'ios_unit_test' => { load: '@build_bazel_rules_ios//rules:test.bzl', rule: 'ios_unit_test' }.freeze
  }.freeze,
}