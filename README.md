The exact list of data types available in a database system can vary depending on the database management system (DBMS) you're using. However, I can provide a list of common data types that are widely supported across many relational database systems like MySQL, PostgreSQL, Oracle, and SQL Server:

1. **Numeric/Integer Types**:
   - `INT` or `INTEGER`: Integer.
   - `SMALLINT`: Small integer.
   - `TINYINT`: Tiny integer.
   - `BIGINT`: Large integer.
   - `NUMERIC(precision, scale)`: Exact numeric with a specified number of digits in the precision and a specified number of decimal places in the scale.
   - `DECIMAL(precision, scale)`: Synonym for `NUMERIC`.

2. **Floating-Point Types**:
   - `FLOAT`: Single-precision floating-point number.
   - `REAL`: Synonym for `FLOAT`.
   - `DOUBLE PRECISION`: Double-precision floating-point number.

3. **Character/String Types**:
   - `CHAR(n)`: Fixed-length character string.
   - `VARCHAR(n)`: Variable-length character string with a maximum length of `n`.
   - `TEXT`: Variable-length character string with no specified maximum length.

4. **Binary Data Types**:
   - `BINARY(n)`: Fixed-length binary string.
   - `VARBINARY(n)`: Variable-length binary string with a maximum length of `n`.
   - `BLOB`: Binary large object for storing binary data.

5. **Date and Time Types**:
   - `DATE`: Date.
   - `TIME`: Time.
   - `DATETIME`: Date and time.
   - `TIMESTAMP`: Date and time, often used for timestamps.

6. **Boolean Type**:
   - `BOOLEAN` or `BOOL`: Represents true or false values.

7. **Enumeration Types**:
   - `ENUM('value1', 'value2', ...)`: Represents a set of predefined values.

8. **Bit Strings**:
   - `BIT(n)`: Fixed-length bit string.
   - `VARBIT(n)`: Variable-length bit string with a maximum length of `n`.

9. **Array Types** (available in some DBMSs):
   - `ARRAY`: Stores an array of values of a specific data type.

10. **User-Defined Types** (available in some DBMSs):
    - These allow you to define custom data types.

11. **Other Types**:
    - `JSON` and `JSONB`: For storing JSON data.
    - `UUID`: Universally unique identifier.
    - `GEOMETRY` and `GEOGRAPHY`: For spatial data (e.g., for GIS applications).

Please note that specific database systems might have additional data types or variations of the above types. It's essential to refer to the documentation of the database system you are using for precise details on supported data types and their characteristics.

---------------------------

The main difference between `INT` and `NUMERIC` (or `INTEGER` and `NUMERIC`) data types in SQL databases is in how they handle numeric values:

1. **`INT` or `INTEGER`**:
   - These data types are used to store integer values (whole numbers).
   - They are typically used for whole numbers without decimal places.
   - The storage size varies depending on the database system but is usually 4 bytes or 8 bytes, depending on whether it's a 32-bit or 64-bit system.

   Example:
   ```sql
   age INT; -- This can store whole numbers like 1, 100, -42, etc.
   ```

2. **`NUMERIC` or `DECIMAL`**:
   - These data types are used to store exact numeric values with a specified precision and scale.
   - `NUMERIC` allows you to specify both the total number of digits (precision) and the number of decimal places (scale).
   - They are suitable for situations where you need to maintain precision in numeric values.
   - `NUMERIC` is a great choice for financial or scientific data where precision is essential.

   Example:
   ```sql
   price NUMERIC(10, 2); -- This can store numbers like 12345.67 with a precision of 10 and 2 decimal places.
   ```

In summary, `INT` or `INTEGER` is used for whole numbers, while `NUMERIC` (or `DECIMAL`) is used for exact numeric values with a specified precision and scale. The choice between them depends on the nature of your data and the level of precision required.