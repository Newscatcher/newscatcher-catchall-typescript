## 1.1.3 - 2026-03-16
* fix: improve type safety for bytes method in BinaryResponse
* Replace generic ReturnType<Response["bytes"]> with explicit Promise<Uint8Array>
* type to provide better TypeScript intellisense and type checking. This change
* makes the return type more predictable and aligns with standard Fetch API
* behavior across different environments.
* Key changes:
* Update bytes method return type from ReturnType<Response["bytes"]> to Promise<Uint8Array>
* Improve type safety and developer experience with explicit typing
* Maintain backward compatibility as underlying behavior remains unchanged
* 🌿 Generated with Fern

