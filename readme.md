# Tezos tokens whitelist

This repo includes a JSON and schema for token lists.

The JSON schema represents the technical specification for a token list which can be used in a dApp interface, such as the QuipuSwap Interface.

## What are token lists?

QuipuSwap Token Lists is a specification for lists of token metadata (e.g. address, decimals, ...) that can be used by any dApp interfaces that needs one or more lists of tokens.

Anyone can create and maintain a token list, as long as they follow the specification.

Specifically an instance of a token list is a [JSON](https://www.json.org/json-en.html) blob that contains a list of
TZIP-12 / TZIP-16 token metadata for use in dApp user interfaces.
Token list JSON must validate against the [JSON schema](https://json-schema.org/) in order to be used in the QuipuSwap Interface.
Tokens on token lists, and token lists themselves, are tagged so that users can easily find tokens.

## Semantic versioning

Lists include a `version` field, which follows [semantic versioning](https://semver.org/).

List versions must follow the rules:

- Increment major version when tokens are removed
- Increment minor version when tokens are added
- Increment patch version when tokens already on the list have minor details changed (name, symbol, logo URL, decimals)

Changing a token address or chain ID is considered both a remove and an add, and should be a major version update.

Note that list versioning is used to improve the user experience, but not for security, i.e. list versions are not meant
to provide protection against malicious updates to a token list; i.e. the list semver is used as a lossy compression
of the diff of list updates. List updates may still be diffed in the client dApp.

## Examples

You can find a simple example of a token list in [schema/example.whitelist.json](schema/example.whitelist.json).
