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
Generally speaking, `did:spv` has similar security properties compared with `did:web`.

### Privacy
None, particulary.
