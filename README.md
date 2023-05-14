# spv's DID Specification
## DID Method Specification
`did:spv` is a deterministic transformation of `did:web` that uses a particular domain.

## DID Format
```
did-spv-format := did:spv:<subdomain>
subdomain      := [a-z0-9_]+
```

The `subdomain` refers to a subdomain of `spv.sh`.

See [did-web](https://w3c-ccg.github.io/did-method-web/).

## DID Operations
See [did-web](https://w3c-ccg.github.io/did-method-web/).

### Create
1. Generate a `did:web`.
2. Remove the TLD and SLD from the domain (must be a subdomain of `spv.sh`), call that the "subdomain".
3. Replace all dots/periods in the subdomain with underscores. `example.domain.spv.sh` becomes `example_domain`.
4. Name the `did:spv` with the subdomain. (`example.spv.sh` becomes `div:spv:example`, `second.example.spv.sh` becomes `did:spv:second_example`, etc.)
5. Update the did document to use the `did:spv` identifier.

### Read
1. Take the subdomain (`div:spv:[THIS PART]`), call that the "subdomain".
2. Replace all underscores in the subdomain with periods. (`an_example` becomes `an.example`, etc.)
3. Append `.spv.sh` to the subdomain. (`an.example` becomes `an.example.spv.sh`, etc).
4. Construct the `did:web` document from the identifier.
5. Update the did document to use the `did:spv` identifier.

### Update
Same steps as Read to transform the identifier, but perform an update operation on the `did:web` identifier.

### Deactivate
Same steps as Update, but perform a Deactivate operation as specified in `did:web`.

## Security and Privacy Considerations
See [did-web](https://w3c-ccg.github.io/did-method-web/).

### Security
As for security, if my domain (spv.sh) either expired, or was compromised, it could lead to issues, as others could take over the resolving of `did:spv` DIDs. As such, I will ensure the renewal of the domain in perpetuity, and will keep my registrar accounts secure. As well, it could present issues for those fully implementing the DID spec, as you would need to ensure internet access is possible, or at least DNS resolution -- this could expose those implementations to exploitation in some form.

### Privacy
`did:spv` will only really be used by me (spv), and as such there are no particular wide-reaching privacy implications for implementers of the DID specification, or general users of those implications. If I (spv) am informed of any others that I have not addressed, I will ensure that they are in a timely manner.

### Conclusion
Hopefully this registration isn't too much of a bother. I'd like it to go through, and as such, if there are any other issues with my DID specification, I will be happy to resolve them.
