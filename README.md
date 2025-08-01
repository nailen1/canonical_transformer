# Canonical Transformer v1.0.0

A Python module for ensuring **structural isomorphism** and **commutative consistency** across data transformations.  
This toolkit provides mathematically reversible mappings between `pandas.DataFrame`, `dict`, `CSV`, and `JSON` formats—preserving data structure, types, and semantics regardless of transformation order.

---

## Features

### Isomorphism Guarantees

- **Bijective Mappings**: Each transformation has a unique and total inverse
- **Structure Integrity**: Index, column types, and ordering are preserved
- **Semantic Equivalence**: Original data meaning remains unchanged

### Commutative Transformations

- **Order-Invariance**: `A → B → C` ≡ `A → C → B`
- **Round-trip Identity**: `T⁻¹ ∘ T(x) = x` for all supported types
- **Transformation Algebra**: Composition, associativity, identity supported

### Supported Formats

- `pandas.DataFrame` ↔ `dict` ↔ `CSV` ↔ `JSON`
- Full interoperability under unified transformation rules
- Automatic type casting and structural validation

---

## Core Capabilities

```
df → dict → csv → json → df      # Exact round-trip equivalence
dict → csv → json → df → dict   # Commutative, isomorphic recovery
```

These transformations preserve:

- Data fidelity (values and types)
- Index and column structure
- Missing value handling (e.g., NaN ≈ None)

---

## Installation

```
pip install canonical-transformer==1.0.0
```

---

## Quick Start

```python
from canonical_transformer import *

df = pd.DataFrame({
    'id': [1, 2, 3],
    'name': ['Alice', 'Bob', 'Charlie'],
    'value': [10.5, -20.3, 30.0]
})

# Commutative round-trip transformation
df2 = map_json_to_df(
           map_csv_to_json(
               map_data_to_csv(
                   map_df_to_data(df), '.', 'out.csv'
               ), '.', 'out.csv'))

assert df.equals(df2)  # True
```

---

## Mathematical Properties

### Isomorphism

- **Injectivity**: Each input maps to a unique output
- **Surjectivity**: All outputs can be traced back to inputs
- **Bijectivity**: Reversible one-to-one mapping

### Commutativity

- **Order Independence**: Transformations commute
- **Associativity**: Grouping doesn’t affect result
- **Identity**: `T⁻¹ ∘ T = id`

### Homomorphism

- **Structure Preservation**: Index, type, ordering maintained
- **Format Standardization**: Consistent formatting across outputs

---

## 📦 Requirements

- Python >= 3.6
- pandas >= 2.2.3
- python-dateutil >= 2.9.0
- pytz >= 2024.2
- typing_extensions >= 4.12.2

---

## 📈 Version History

### v1.0.0

- Structural isomorphism guaranteed
- Bidirectional reversible transformations
- Full commutative consistency
- Format and type standardization

### v0.2.x

- Number formatting utilities
- Sign-preserving float formatting

---

## 👤 Author

**June Young Park**  
AI Systems Architect @ LIFE Asset Management  
📧 juneyoungpaak@gmail.com  
📍 TWO IFC, Yeouido, Seoul

> LIFE Asset Management is a hedge fund management firm that integrates value investing and engagement strategies with quantitative modeling and AI infrastructure.

---

## 📖 License

MIT License – see `LICENSE` file for details.

---
