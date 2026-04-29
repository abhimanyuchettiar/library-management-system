# Normalisation Notes

## Unnormalised Form (UNF)
TODO: Show the flat table before normalisation

## First Normal Form (1NF)
**Violation:** authors column contained comma-separated values
**Fix:** Extracted to AUTHOR table + BOOK_AUTHOR junction table

## Second Normal Form (2NF)
**Violation:** author_nationality depended only on author_id in a composite-key table
**Fix:** Moved to separate AUTHOR table

## Third Normal Form (3NF)
**Violation:** publisher_city and publisher_country transitively dependent via publisher_name
**Fix:** Extracted to PUBLISHER table

## Boyce-Codd Normal Form (BCNF)
TODO: Document all functional dependencies and verify every determinant is a superkey
