```
  _   _    _  _____ ____   _  _____ ____  
 | \ | |  / \|_   _/ ___| | |/ ( _ ) ___| 
 |  \| | / _ \ | | \___ \ | ' // _ \___ \ 
 | |\  |/ ___ \| |  ___) || . \ (_) |__) |
 |_| \_/_/   \_\_| |____(_)_|\_\___/____/ 
                                          
```
[![License][License-Image]][License-Url]
[![Version](https://d25lcipzij17d.cloudfront.net/badge.svg?id=go&type=5&v=0.1.0)](https://github.com/nats-io/k8s/releases/tag/v0.1.0)

[License-Url]: https://www.apache.org/licenses/LICENSE-2.0
[License-Image]: https://img.shields.io/badge/License-Apache2-blue.svg

# Running NATS on K8S

In this repository you can find several examples of how to deploy NATS, NATS Streaming 
and other tools from the NATS ecosystem on Kubernetes.

### Getting started

The fastest and easiest way to get started is with just one shell command:

```sh
curl -sSL https://nats-io.github.io/k8s/setup.sh | sh
```

This will run a `nats-setup` container with the [required policy](https://github.com/nats-io/k8s/blob/master/setup/bootstrap-policy.yml)
and deploy a NATS cluster on Kubernetes with external access, TLS and
decentralized authorization.

By default, the installer will deploy the [Prometheus Operator](https://github.com/coreos/prometheus-operator) and the
[Cert Manager](https://github.com/jetstack/cert-manager) for metrics and TLS support, and the NATS instances will
also bind the 4222 host port for external access.

You can customize the installer to install without TLS or without Auth
to have a simpler setup as follows:

```sh
# Disable TLS
curl -sSL https://nats-io.github.io/k8s/setup.sh | sh -s -- --without-tls

# Disable Auth and TLS (also disables NATS surveyor and NATS Streaming)
curl -sSL https://nats-io.github.io/k8s/setup.sh | sh -s -- --without-tls --without-auth
```

**Note**: Since NATS Streaming will be running as a leafnode to NATS
(under the STAN account) and that [NATS Surveyor](https://github.com/nats-io/nats-surveyor) 
requires the system account to monitor events, disabling auth also means that NATS
Streaming and NATS Surveyor based monitoring will be disabled.

#### Example

[![asciicast](https://asciinema.org/a/282135.svg)](https://asciinema.org/a/282135)
