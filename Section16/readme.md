# SSL Discovery with Host and TLS
- implement 2 demos
- By Default Ingress can take the available certificate for the host name we gave i.e automatically it will take that certificate and associate with the ingress service(loadbalancer).We explecitly don't need to give certificate arn in the ingress service. - Host based
- The controller will attempt to discover TLS certificates from the tls field in Ingress and host field in Ingress rules.
- we need to explicitly specify to use HTTPS listner with listen-ports annotation.