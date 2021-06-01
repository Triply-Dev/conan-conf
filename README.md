# Conan configuration

Easy installation of Conan configuration.

## Installation

```sh
conan config install https://github.com/Triply-Dev/conan-conf.git --type git
```

## Open issues

### Modern Conan names give errors in Gitlab

It is common practice to use Conan dependency names without specifying
the user and channel parts explicitly.  Unfortunately, Gitlab
currently emits the following error when such dependency names:

```
ERROR: {"error":"package_username is invalid, package_channel is invalid"}. [Remote: gitlab]
```

This is [a known issue of
Gitlab](https://gitlab.com/gitlab-org/gitlab/-/issues/271400) that is
not yet fixed.

This effectively means that we cannot use Gitlab for Conan packages
for projects that use at least one package from Conan Center and at
least one package from Triply.

### JSON configuration format not yet supported

In recent Conan versions configuration file `remotes.json` is used
instead of the old configuration file `remotes.txt` internally.
Unfortunately, the Conan 1.22.2 configuration command does not yet
support this modern file format:

```sh
ERROR: remotes.json install is not supported yet. Use 'remotes.txt'
```

Let's wait for a newer version of Conan and see whether we can start
using the JSON variant of the configuration file.  It has the
following structure:

```json
{
  "remotes": [
    {
      "name": "conan-center",
      "url": "https://conan.bintray.com",
      "verify_ssl": true
    },
    {
      "name": "bincrafters",
      "url": "https://api.bintray.com/conan/bincrafters/public-conan",
      "verify_ssl": true
    },
    {
      "name": "triply",
      "url": "https://triplybv.jfrog.io/artifactory/api/conan/triply-conan-local",
      "verify_ssl": true
    }
  ]
}
```
