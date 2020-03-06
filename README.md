# Conan configuration

Easy installation of Conan configuration.

## Installation

```sh
conan config install https://github.com/Triply-Dev/conan-conf.git --type git
```

## Open issues
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
      "name": "bincrafters",
      "url": "https://api.bintray.com/conan/bincrafters/public-conan",
      "verify_ssl": true
    },
    {
      "name": "conan-center",
      "url": "https://conan.bintray.com",
      "verify_ssl": true
    },
    {
      "name": "triply",
      "url": "https://triply.jfrog.io/triply/api/conan/conan-local",
      "verify_ssl": true
    }
  ]
}
```
