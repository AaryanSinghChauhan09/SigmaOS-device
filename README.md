# SigmaOS Device

Rust library for device and driver management. The exported API includes a
`DeviceManager`; the source tree also contains device lifecycle, PCI, storage,
network, graphics, and driver-management modules.

## Implementation limits

Some current device implementations are placeholders: for example, the legacy
and modern device examples return zero-filled read buffers and accept writes
without touching hardware. Other modules expose simulated devices or
management models. These APIs are not evidence of real device discovery,
hardware access, or driver installation. Do not use them for production I/O or
claim platform support without reviewing the specific path.

## Integration requirements

Document platform and device scope, permission boundaries, resource ownership,
DMA and interrupt assumptions, and cleanup on failure. Keep discovery separate
from policy and user interface. Validate hardware-facing behavior against a
named emulator or supported device before reporting it as operational.

## Development

The crate depends on `SigmaOS-kernel` through a sibling path dependency. CI
resolves SigmaOS path dependencies and runs `cargo test --all-targets --locked`.
