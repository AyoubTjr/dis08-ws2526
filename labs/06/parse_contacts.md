# parse_contacts.md
Quelle: `csv/contacts.csv`

## 1) Extract all email addresses
```bash
grep -Eo '[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}' csv/contacts.csv
```
---
## 2) Extract all phone numbers
```bash
grep -Eo '(\([0-9]{3}\)[[:space:]]*[0-9]{3}[-.[:space:]]*[0-9]{4}|[0-9]{3}[-.[:space:]]*[0-9]{3}[-.[:space:]]*[0-9]{4})' csv/contacts.csv
```
---
## 3) Extract all names that start with the letter ‘J’
```bash
grep -Eo '\bJ[A-Za-z]+[[:space:]]+[A-Za-z]+' csv/contacts.csv
```
---
## 4) Extract all street names that contain the word ‘St’
```bash
grep -Eo '\b[0-9A-Za-z .-]*St\.?\b' csv/contacts.csv
```
---
## 5) Extract the last names of all people
```bash
grep -Eo '\b[A-Za-z]+[[:space:]]+[A-Za-z]+\b' csv/contacts.csv | awk '{print $2}'
```
---
## 6) Extract all email domains (part after the @ sign)
```bash
grep -Eo '[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}' csv/contacts.csv | sed -E 's/.*@//'
```
---
## 7) Find all entries where the phone number ends with ‘7’
```bash
grep -Eo '(\([0-9]{3}\)[[:space:]]*[0-9]{3}[-.[:space:]]*[0-9]{4}|[0-9]{3}[-.[:space:]]*[0-9]{3}[-.[:space:]]*[0-9]{4})' csv/contacts.csv | grep -E '7$'
```
---
## 8) Extract all instances of first names that end with the letter ‘e’
```bash
grep -Eo '\b[A-Za-z]+[[:space:]]+[A-Za-z]+\b' csv/contacts.csv | awk '{print $1}' | grep -E 'e$'
