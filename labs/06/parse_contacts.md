# parse_contacts.md
Quelle: `csv/contacts.csv`

## 1) Extract all email addresses
```bash
grep -Eo '[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}' csv/contacts.csv

grep -Eo '($begin:math:text$\[0\-9\]\{3\}$end:math:text$[[:space:]]*[0-9]{3}[-.[:space:]]*[0-9]{4}|[0-9]{3}[-.[:space:]]*[0-9]{3}[-.[:space:]]*[0-9]{4})' csv/contacts.csv

grep -Eo '\bJ[A-Za-z]+[[:space:]]+[A-Za-z]+' csv/contacts.csv

grep -Eo '\b[0-9A-Za-z .-]*St\.?\b' csv/contacts.csv

grep -Eo '\b[A-Za-z]+[[:space:]]+[A-Za-z]+\b' csv/contacts.csv | awk '{print $2}'

grep -Eo '[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}' csv/contacts.csv | sed -E 's/.*@//'

grep -Eo '($begin:math:text$\[0\-9\]\{3\}$end:math:text$[[:space:]]*[0-9]{3}[-.[:space:]]*[0-9]{4}|[0-9]{3}[-.[:space:]]*[0-9]{3}[-.[:space:]]*[0-9]{4})' csv/contacts.csv | grep -E '7$'

grep -Eo '\b[A-Za-z]+[[:space:]]+[A-Za-z]+\b' csv/contacts.csv | awk '{print $1}' | grep -E 'e$'
