```mermaid
flowchart
    A[Client: Holds client cert, key, and CA]
    B[Client: Initiates TLS handshake]
    C[Server: Holds server cert, key, and CA]
    D[Server: Receives TLS handshake (with client cert)]
    E[Server: Validates client certificate chain<br/>(ensures signed by root CA)]
    F[Server: Sends its certificate to client]
    G[Client: Receives server certificate]
    H[Client: Validates server certificate chain<br/>(ensures signed by root CA)]
    I[Client: Checks server certificate CN<br/>against SslTargetNameOverride]
    J[Both: Decide to accept or reject connection]

A -> B
B -> D
D -> E
E -> F
F -> G
G -> H
H -> I
I -> J
```
