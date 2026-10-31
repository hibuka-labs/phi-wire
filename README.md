# phi-wire

The provider wire for the [phi family](https://github.com/hibuka-labs/phi-agent):
one JSON-lines protocol, one correlation discipline, one transport.

A capability pack runs as a separate process. The host speaks to it over
stdin/stdout, one JSON object per line:

```json
{"op": "describe", "_request_id": 1, "timeout_ms": 30000}
{"_request_id": 1, "result": {"capabilities": ["b.screenshot"]}}
```

* **`phi-wire-protocol`** — the message shapes: `Request`, `Reply`, `Error`,
  `Event`. Versioned, platform-free.
* **`phi-wire-adapter`** — the `Provider` trait shared by clients and platform
  adapters, plus the local host file/process helpers.
* **`phi-wire-client`** — `ProcessClient`: the correlated JSON-lines
  subprocess transport. A cancelled request is never replayed.

## Why this exists

Device and browser capability packs are separate processes on purpose: the
audit gate must not be bypassable from inside a worker. That means every
request crosses a process boundary, and the boundary needs one wire — not one
per pack. This workspace is that wire.

## Fork notice

These crates are a fork of the `mu-protocol` / `mu-adapter` / `mu-client`
crates from [Tongyi-MAI/OpenGCUA](https://github.com/Tongyi-MAI/OpenGCUA)
(Apache-2.0). See [NOTICE](NOTICE) for the attribution and the exact list of
changes. The fork changes packaging metadata only; protocol and transport
logic are unchanged.

## License

Apache-2.0.
