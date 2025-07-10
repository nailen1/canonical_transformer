# Canonical Transformer v1.0.0

A Python module for preserving **isomorphisms** between data transformations, enabling **commutative input/output operations** across different data types and formats. This module ensures that data transformations maintain their mathematical properties and can be performed in any order while preserving the original structure.

## Features

### **Isomorphism Preservation**

- **Mathematical Consistency**: All transformations preserve the underlying mathematical structure
- **Bidirectional Mapping**: Every transformation has a perfect inverse
- **Structure Preservation**: Data integrity maintained across all conversions

### **Commutative Data Operations**

- **Order Independence**: Transformations can be performed in any sequence
- **Round-trip Consistency**: A → B → A returns the original data unchanged
- **Commutative Property**: (A → B) → C = A → (B → C)

### **Supported Data Types & Formats**

- **DataFrame** ↔ **Dictionary** ↔ **CSV** ↔ **JSON**
- **Full Commutativity**: Any combination of transformations preserves data integrity
- **Type Safety**: Automatic type inference and validation
- **Format Consistency**: Standardized formatting across all outputs

## Core Capabilities

### **Commutative Transformations**

```python
# These operations are commutative and preserve isomorphism
df → dict → csv → json → df  # Returns original DataFrame
dict → csv → json → df → dict  # Returns original Dictionary
```

### **Isomorphic Mappings**

- **DataFrame ↔ Dictionary**: Bidirectional with structure preservation
- **DataFrame ↔ CSV**: File I/O with format consistency
- **DataFrame ↔ JSON**: Serialization with type preservation
- **Dictionary ↔ CSV**: Direct file operations
- **Dictionary ↔ JSON**: Native serialization

## Installation

```bash
pip install canonical-transformer==1.0.0
```

## Quick Start

```python
from canonical_transformer import *

# Create sample data
df = pd.DataFrame({
    'id': [1, 2, 3],
    'name': ['Alice', 'Bob', 'Charlie'],
    'value': [10.5, -20.3, 30.0]
})

# Demonstrate commutative operations
# DataFrame → Dictionary → CSV → JSON → DataFrame
dict_data = map_df_to_data(df)
csv_file = map_data_to_csv(dict_data, './', 'output.csv')
json_data = map_csv_to_json('./', 'output.csv')
final_df = map_json_to_df(json_data)

# Verify isomorphism preservation
assert df.equals(final_df)  # True - perfect round-trip

# Demonstrate commutativity
# Different order, same result
json_data2 = map_df_to_json(df)
csv_file2 = map_json_to_csv(json_data2, './', 'output2.csv')
dict_data2 = map_csv_to_data('./', 'output2.csv')
final_df2 = map_data_to_df(dict_data2)

assert df.equals(final_df2)  # True - commutative property holds
```

## Mathematical Properties

### **Isomorphism**

- **Injective**: Each input maps to a unique output
- **Surjective**: Every possible output has a corresponding input
- **Bijective**: Perfect one-to-one correspondence

### **Commutativity**

- **Order Independence**: Transformation sequence doesn't affect final result
- **Associative Property**: Grouping of operations doesn't matter
- **Identity Preservation**: Original data structure is maintained

### **Homomorphism**

- **Structure Preservation**: Relationships between data elements are maintained
- **Type Consistency**: Data types are preserved across transformations
- **Format Standardization**: Consistent output formatting

## Advanced Usage

### **Batch Operations**

```python
# Process multiple files with commutative operations
files = ['data1.csv', 'data2.json', 'data3.csv']

for file in files:
    if file.endswith('.csv'):
        df = load_csv('./', file)
        json_data = map_df_to_json(df)
        # All operations preserve isomorphism
    elif file.endswith('.json'):
        df = map_json_to_df(load_json('./', file))
        csv_data = map_df_to_csv(df, './', file.replace('.json', '.csv'))
```

### **Data Validation**

```python
# Verify isomorphism preservation
original_df = create_sample_dataframe()
transformed_data = map_df_to_data(original_df)
restored_df = map_data_to_df(transformed_data)

# Mathematical verification
assert original_df.equals(restored_df)
assert original_df.dtypes.equals(restored_df.dtypes)
assert original_df.index.equals(restored_df.index)
```

## Requirements

- Python >= 3.6
- pandas >= 2.2.3
- python-dateutil >= 2.9.0
- pytz >= 2024.2
- typing_extensions >= 4.12.2

## Version History

### v1.0.0 - Major Release

- **Isomorphism Preservation**: All transformations now preserve mathematical structure
- **Commutative Operations**: Data transformations can be performed in any order
- **Bidirectional Mapping**: Perfect inverse operations for all transformations
- **Structure Preservation**: Data integrity maintained across all conversions
- **Mathematical Consistency**: Formal mathematical properties implemented
- **Type Safety**: Enhanced type inference and validation
- **Format Standardization**: Consistent output formatting across all operations

### Previous Versions

- v0.2.7: Enhanced number formatting with non-integer decimal_digits
- v0.2.6: Added number formatting utilities with explicit sign display
- v0.2.5: Initial number formatting implementation

## Mathematical Foundation

This module is built on mathematical principles:

- **Category Theory**: Transformations as morphisms between data categories
- **Group Theory**: Commutative operations forming algebraic structures
- **Set Theory**: Isomorphic mappings preserving set properties
- **Abstract Algebra**: Homomorphic properties in data transformations

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Author

**June Young Park**  
AI Management Development Team Lead & Quant Strategist at LIFE Asset Management

LIFE Asset Management is a hedge fund management firm that integrates value investing and engagement strategies with quantitative approaches and financial technology, headquartered in Seoul, South Korea.

## Contact

- Email: juneyoungpaak@gmail.com
- Location: TWO IFC, Yeouido, Seoul

---

**Note**: This release introduces isomorphism preservation and commutative properties for data transformations, ensuring mathematical consistency across all operations.
