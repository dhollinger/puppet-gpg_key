# gpg_key [![Build Status](https://travis-ci.org/dhollinger/puppet-gpg_key.svg?branch=master)](https://travis-ci.org/dhollinger/puppet-gpg_key)

The gpg_key module lets you manage GPG keys with Puppet.

Currently the only provider is to import RPM GPG keys.

NOTE:
The 0.0.4 release fixes the Facter issue with the removed fact method. 
Treydock fixed this in his code, I am just releasing it to the Forge.

## Compatibility

| Puppet Versions   | < 2.6 | 2.6 | 2.7     | 3.x     |4.x      |
|:-----------------:|:-----:|:---:|:-------:|:-------:|:-------:|
| **gpg_key 0.0.5** | no    | no  | no      | **yes** | **yes** |

## Support

Tested using

* CentOS 6.x
* CentOS 7.x

## Usage

### gpg_key

Installs a GPG key at the given path.  This type autorequires the file resource in `path`

    file { 'RPM-GPG-KEY-foo':
      ensure  => present,
      path    => '/etc/pki/rpm-gpg/RPM-GPG-KEY-foo',
      source  => 'file:///modules/foo/RPM-GPG-KEY-foo',
    }

    gpg_key { 'foo':
      path  => '/etc/pki/rpm-gpg/RPM-GPG-KEY-foo',
    }

## Reference

Types:

* [gpg_key](#type-gpg_key)

### Type: gpg_key

This type provides the capability to manage GPG keys within Puppet.

####`ensure`

Indicates if the GPG key should be imported or removed.

Can either be `present` or `absent`.  Defaults to `present`.

####`path`

The path of the GPG key to import.

This value must be an absolute filesystem path.

## Development

### Testing

Make sure you have:

* rake
* bundler

Install the necessary gems:

    bundle install

Run the tests from root of the source code:

    bundle exec rake test
