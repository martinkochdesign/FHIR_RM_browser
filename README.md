# 🔥 FHIR Reference Model Browser

An interactive, browser-based tool for exploring the FHIR Reference Model — browse any FHIR resource or data type with full element metadata including descriptions, bindings, value sets, cardinality, types, constraints, and mappings.

**👉 [Live Demo](https://martinkochdesign.github.io/FHIR_RM_browser)**

![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)
![FHIR](https://img.shields.io/badge/FHIR-R4%20%7C%20R4B%20%7C%20R5-orange.svg)

---

## What It Does

The FHIR Reference Model Browser lets you visually explore the complete structure of any FHIR resource or data type, loaded directly from the official HL7 `definitions.json.zip` files. Unlike the raw JSON schema, this tool preserves all the rich metadata from the StructureDefinitions:

- **Full resource tree** — all elements with expandable hierarchy
- **Descriptions** — short, definition, comments, and requirements for every element
- **Bindings** — strength (required/extensible/preferred/example) with clickable ValueSet links
- **Cardinality** — exact `min..max` from the element definitions
- **Types** — full type list with target profiles (e.g., `Reference(Patient, Practitioner)`)
- **Clickable data types** — click any complex type (HumanName, CodeableConcept, Identifier, etc.) to explore its structure in a popup
- **Constraints** — all FHIR invariants with key, severity, and human-readable description
- **Mappings** — v2, RIM, CDA, and other standard mappings
- **Flags** — mustSupport, isModifier, isSummary clearly indicated
- **Direct spec links** — one-click navigation to the hl7.org definition page for any element
- **Copy FHIR paths** — one-click copy of any element path
- **Multi-version support** — load R4, R4B, and R5 side by side, switch between them
- **Browser caching** — definitions are cached in IndexedDB, load each version only once
- **FHIR version auto-detection** — automatically identifies which version you loaded

---

## How to Use

### Step 1: Download Base Definitions

Download the `definitions.json.zip` for the FHIR version(s) you want to explore:

- [⬇ R4 (4.0.1) — definitions.json.zip](https://hl7.org/fhir/R4/definitions.json.zip)
- [⬇ R4B (4.3.0) — definitions.json.zip](https://hl7.org/fhir/R4B/definitions.json.zip)
- [⬇ R5 (5.0.0) — definitions.json.zip](https://hl7.org/fhir/R5/definitions.json.zip)

### Step 2: Load into the Browser

1. Open the [FHIR RM Browser](https://martinkochdesign.github.io/FHIR_RM_browser).
2. Click **📂 Load definitions ZIP** and select the downloaded file.
3. Wait for parsing (a few seconds) — the version is auto-detected and shown.
4. You only need to do this once per version — definitions are cached in your browser.

### Step 3: Explore

- **Search** for any resource (Patient, Observation, MedicationRequest…) using the search bar.
- **Expand** nodes to drill into the element hierarchy.
- **Click** any element to see full details in the side panel.
- **Click type names** (e.g., `HumanName`, `CodeableConcept`) to explore data types in a popup.
- **Click 📖 ValueSet links** in bindings to jump to the HL7 spec.
- **Click 🔗 View on hl7.org** to see the official definition page for any element.
- **Copy paths** with the 📋 button for use in FHIRPath, AQL, or mapping documents.

---

## Visual Guide

| Indicator | Meaning |
|-----------|---------|
| 🔴 Red dot | Required element (min > 0) |
| Colored binding dot | Binding strength: 🔴 required, 🟠 extensible, 🔵 preferred, ⚫ example |
| **S** green badge | String type |
| **#** orange badge | Numeric type |
| **B** red badge | Boolean type |
| **→** teal badge | Reference type |
| **C** pink badge | Code/CodeableConcept type |
| **{}** purple badge | BackboneElement (has children) |
| **[]** violet badge | Array (max = *) |
| Dashed underline on type | Clickable — opens data type popup |

---

## Example: Exploring Patient.gender

1. Search for **Patient** and select it.
2. Expand the tree and click on **gender**.
3. In the detail panel you'll see:
   - **Short**: "male | female | other | unknown"
   - **Type**: `code`
   - **Cardinality**: `0..1 (optional)`
   - **Binding**: 🔴 required — [AdministrativeGender](https://hl7.org/fhir/R4/valueset-administrative-gender.html)
   - **Constraints**: ele-1 (error) — "All FHIR elements must have a @value or children"
   - **🔗 View on hl7.org** — direct link to the spec

This is the kind of rich, contextual information that gets lost when using only the JSON schema file.

---

## Schema vs. Definitions — Why This Tool Uses Definitions

| Feature | `fhir.schema.json` | `definitions.json.zip` (this tool) |
|---------|--------------------|------------------------------------|
| Descriptions | Basic `description` only | Full `short`, `definition`, `comment`, `requirements` |
| Bindings | ❌ None | ✅ Strength + ValueSet link |
| Cardinality | Inferred from `required[]` | Exact `min..max` per element |
| Types | Just `$ref` name | Full type list with target profiles |
| Constraints | ❌ None | ✅ All invariants (key, severity, human text) |
| Mappings | ❌ None | ✅ v2, RIM, CDA, etc. |
| Flags | ❌ None | ✅ mustSupport, isModifier, isSummary |
| Spec links | ❌ None | ✅ Direct link to hl7.org |

---

## Technical Details

- **Pure client-side** — no server, no data leaves your browser
- **No installation required** — just open the page
- **IndexedDB caching** — load definitions once, they persist across sessions
- **Multi-version** — load multiple FHIR versions and switch between them
- **Dependencies** (loaded from CDN):
  - [JSZip](https://stuk.github.io/jszip/) — for ZIP extraction

---

## Related Tools

- **[FHIR Profile Explorer](https://martinkochdesign.github.io/FHIR_profile_explorer/)** — explore Simplifier Implementation Guide packages with differential highlighting, Must Support flags, and inline examples

---

## Author

**Martin A. Koch, PhD**  
Servei Català de la Salut / CatSalut  
📧 martinandreaskoch@catsalut.cat

---

## License

This project is licensed under the [Apache License 2.0](LICENSE).
© 2026 Servei Català de la Salut / CatSalut