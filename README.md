# Peppol BIS Billing 3.0 & EN 16931 E-Invoice Engine — Rust Client Crate

[![Crates.io](https://img.shields.io/crates/v/stanzaapi-peppol-validator.svg)](https://crates.io/crates/stanzaapi-peppol-validator)
[![Documentation](https://docs.rs/stanzaapi-peppol-validator/badge.svg)](https://docs.rs/stanzaapi-peppol-validator)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Stanza API](https://img.shields.io/badge/Powered%20by-Stanza-blue)](https://stanzaapi.com)

> Sub-5ms Peppol BIS Billing 3.0 & EN 16931 e-invoice validation and XML-to-JSON parsing supporting OASIS UBL 2.1 and UN/CEFACT CII.

Official high-performance, asynchronous Rust client library for **Peppol BIS Billing 3.0 & EN 16931 E-Invoice Engine**, built on the [Stanza Micro-API Network](https://stanzaapi.com). Uses pure Rustls TLS (zero C/OpenSSL dependencies) and Tokio for maximum concurrency and safety.

* 🌐 **Online Interactive Sandbox:** [Test your inputs live](https://stanzaapi.com/tools/peppol-validator)
* 📚 **API Reference & Schemas:** [View documentation on Stanza](https://stanzaapi.com/tools/peppol-validator)
* ⚡ **Platform Overview:** [Explore the Stanza Developer Network](https://stanzaapi.com)

---

## 📦 Installation

Add to your `Cargo.toml`:

```toml
[dependencies]
stanzaapi-peppol-validator = "1.0.0"
tokio = { version = "1.0", features = ["full"] }
```

Or use `cargo add`:

```bash
cargo add stanzaapi-peppol-validator
```

---

## 🚀 Quickstart

```rust
use stanzaapi_peppol_validator::PeppolValidatorClient;

#[tokio::main]
async fn main() -> Result<(), Box<dyn std::error::Error>> {
    // Reads STANZA_API_KEY from environment automatically
    let client = PeppolValidatorClient::new(None, None);

    let response = client.validate("<Invoice xmlns=\"urn:oasis:names:specification:ubl:schema:xsd:Invoice-2\">...</Invoice>").await?;

    if response.success {
        println!("Verification Success: {:?}", response.data);
    } else {
        eprintln!("Validation Error: {:?}", response.error);
    }

    Ok(())
}
```

---

## 📄 Example Response

```json
{
  "success": true,
  "data": {
    "valid": true,
    "profile": "urn:fdc:peppol.eu:2017:poacc:billing:01:1.0",
    "invoice_number": "INV-2026-001"
  }
}
```

---

## 🔗 Useful Links

* [Peppol BIS Billing 3.0 & EN 16931 E-Invoice Engine Interactive Sandbox](https://stanzaapi.com/tools/peppol-validator)
* [Stanza Developer Directory](https://stanzaapi.com)
* [Source Code & Issue Tracker](https://github.com/stanzaapi/peppol-validator-rust)

## 📄 License

MIT © Stanza — Powered by [Stanza](https://stanzaapi.com).
