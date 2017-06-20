---
permalink: /RDATKit/docs/
level: 2
prev: install/
---

## _RDAT_ File Handling

To read an _RDAT_ file into session:

```python
import rdatkit

# create RDATFile instance
rdat = rdatkit.RDATFile()
# load RDAT file
rdat.load(open('myRDATFile.rdat'))
```

The `RDATFile` object has a dictionary constructs that contains all of the expected information for each construct in the file. For convenience, data are saved as dictionaries of matrices (indexed by the construct names): `values`, `xsels`, `errors`, and `traces`, respectively. You can use the `save()` method of the `RDATFile` to write back the changes you have made to the data.

To validate the data contained in a _RDAT_ file (e.g. checking that the sequence positions specified in `seqpos` are the same length as the peak values called), simply call:

```python
# validate RDAT file
rdat.validate()
```

This will produce a bunch of warnings if the file suffers inconsistencies.

Finally, `RDATFile` objects can be converted to `ISATABFile` objects for format convertions:

```python
# convert RDAT to ISATAB
isatab = rdat.toISATAB()
```

<hr/>

## _ISATAB_ File Handling

ISATAB files are handled in a similar way in _Python_, but under `ISATABFile` class instead of `RDATFile` class. Here is a summary script of _ISATAB_ file handling similar to what has been previously demonstrated with _RDAT_ file:

```python
import rdatkit

# create ISATABFile instance
isatab = rdatkit.ISATABFile()
# load ISATAB file
filename = 'myISATABfile.xls'
isatab.load(filename, type='xls')
# load ISATAB files from directory
dirname = 'isatab_files/'
isatab.load(dirname, type='dir')
# validate ISATAB file
isatab.validate()
# write to ISATAB file
isatab.save('test.xls', type='xls')
```

The `type` option in the `save()` and `load()` methods specifies whether to save/load from/to an excel **.xls** file or a directory of **.csv** files (one for each sheet).

For more information about the _ISATAB_ file specification, specifically used in the RNA mapping field, visit [SNRNASM](http://ribosnitch.bio.unc.edu/snrnasm/).
