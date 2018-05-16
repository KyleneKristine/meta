Metadata
======
Useful regex and json used to update our records using sierra and/or marcedit.

<br>
<br>

## Export data from MRC
```python
import pymarc
from pymarc import MARCReader
with open(r'C:/path/file', 'rb') as fh: #Select file containing needed information (ex. C:/Users/name/Desktop/test.mrc)
  reader = MARCReader(fh)
  inlist = []
  for record in reader:
    try:
      print(record['010']['a']) #change as needed; line isn't necessary and can be deleted if prefered
      inlist.append(record['010']['a']+'\n') #repeat record number/subfield change here as well
    except TypeError:
      print('Error')
    with open(r'C:/path/file', 'w') as txt: #different file than above, can create brand new file this way. (ex. C:/Users/name/Desktop/test.txt')
      txt.writelines(inlist)
```
<br>

<br>

## Saved Sierra Queries
Mostly Beginning of the Month Create Lists

### Aux Amateurs Shelf Ready
```json
{"queries": [
{"target": {"record": {"type": "bib"}, "field": {"marcTag": "910"}}, "expr": {"op": "has", "operands" :["Aux Amateurs shelf-ready", ""]}}, 
"and", 
{"target": {"record": {"type": "bib"}, "id": 28}, "expr": {"op": "between", "operands": ["02-28-2018", "04-01-2018"]}}, 
"and", 
{"target": {"record": {"type": "bib"}, "field": {"marcTag": "993"}}, "expr": {"op": "all_fields_not_have", "operands": ["ftp", ""]}}
]}
```
<br>

### Casalini
```json
{"queries": [ 
{"target": {"record": {"type": "bib"}, "field": {"marcTag": "910"}}, "expr": {"op": "has", "operands": ["Casalini",""]}}, 
"and", 
{"target": {"record":{"type":"bib"},"field":{"marcTag":"993"}},"expr":{"op":"all_fields_not_have","operands":["ftp",""]}},
"and",
{"target":{"record":{"type":"bib"},"id":28},"expr":{"op":"between","operands":["01-31-2018","04-01-2018"]}}
]}
```
<br>

### Coutts Shelf Ready
```json
{"queries":[
{"target":{"record":{"type":"bib"},"field":{"marcTag":"910"}},"expr":{"op":"has","operands":["Coutts",""]}},
"and",
{"target":{"record":{"type":"bib"},"id":28},"expr":{"op":"between","operands":["01-31-2018","04-01-2018"]}},
"and",
{"target":{"record":{"type":"bib"},"field":{"marcTag":"993"}},"expr":{"op":"all_fields_not_have","operands":["ftp",""]}}
]}
```
<br>

### OCLC Loads
```json
{"queries":[
{"target":{"record":{"type":"bib"},"id": 31},"expr":{"op":"equals","operands":["u",""]}}
]}
```
<br>

### Backstage
```json
{"queries":[
{"target":{"record":{"type":"bib"},"id":28},"expr":{"op":"between","operands":["03-01-2018","04-01-2018"]}},
"and",
{"target":{"record":{"type":"bib"},"field":{"marcTag":"910"}},"expr":{"op":"all_fields_not_have","operands":["backstage",""]}},
"and",
{"target":{"record":{"type":"bib"},"field":{"marcTag":"910"}},"expr":{"op":"all_fields_not_have","operands":["serials solutions",""]}},
"and",
{"target":{"record":{"type":"bib"},"field":{"marcTag":"910"}},"expr":{"op":"all_fields_not_have","operands":["jstordda",""]}},
"and",
{"target":{"record":{"type":"bib"},"field":{"marcTag":"856"}},"expr":{"op":"all_fields_not_have","operands":["ebrary",""]}},
"and",
{"target":{"record":{"type":"bib"},"tag":"a"},"expr":{"op":"all_fields_not_have","operands":["gobi sciences dda",""]}},
"and",
{"target":{"record":{"type":"bib"},"id":26},"expr":{"op":"all_fields_not_have","operands":["j0001",""]}},
"and",
{"target":{"record":{"type":"bib"},"specialField":52},"expr":{"op":"all_fields_not_have","operands":["z",""]}},
"and",
{"target":{"record":{"type":"bib"},"specialField":52},"expr":{"op":"all_fields_not_have","operands":["u",""]}},
"and",
{"target":{"record":{"type":"bib"},"specialField":31},"expr":{"op":"not_equal","operands":["n",""]}},
"and",
{"target":{"record":{"type":"bib"},"field":{"marcTag":"001"}},"expr":{"op":"all_fields_not_have","operands":["asp",""]}},
"and",
{"target":{"record":{"type":"bib"},"field":{"marcTag":"910"}},"expr":{"op":"all_fields_not_have","operands":["lexisnexis",""]}},
"and",
{"target":{"record":{"type":"bib"},"field":{"marcTag":"910"}},"expr":{"op":"all_fields_not_have","operands":["ebsco academic",""]}},
"and",
{"target":{"record":{"type":"bib"},"field":{"marcTag":"910"}},"expr":{"op":"all_fields_not_have","operands":["hstalks",""]}},
"and",
{"target":{"record":{"type":"bib"},"field":{"marcTag":"910"}},"expr":{"op":"all_fields_not_have","operands":["kanopy",""]}}
]}
```
