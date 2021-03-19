# 化学标识符(Chemical Identifier)获得和转换
### 
## 一、通过在线的网络服务器
### 1. Chemical Identifier Resolver
来自美国国立卫生研究院的[NCI/CADD group](https://cactus.nci.nih.gov/)，主页为(https://cactus.nci.nih.gov/chemical/structure)。可以通过该服务器的URL API，快速批量的获取化学标识符。

URL API scheme:
```
https://cactus.nci.nih.gov/chemical/structure/"structure identifier"/"representation"
```
Example: Chemical name to Standard InChIKey:
```
https://cactus.nci.nih.gov/chemical/structure/aspirin/stdinchikey
```
**注意**：输入中的特殊字符如`#`需要进行转换成别的字符，不然会报错。

**Note:** Triple bonds in SMILES strings represented by '#' have to be URL-escaped as '%23' (e.g. the SMILES string of ethyne has to be specified as 'C%23C' instead of 'C#C' if encoded as part of a URL). Similarly, question marks, which can occur in InChI, need to be URL-escaped as %3F.

**通过python的网络请求(request):**
```python
import requests

opsin = 'https://cactus.nci.nih.gov/chemical/structure/{0}/{1}'
ide = 'C#C'  # SMILES of ethyne
ide = ide.replace('#', '%23')
rep = 'stdinchikey'  # the desired output is StdInChIKey
# for more representations
"""
rep = 'smiles'      # the desired output is SMILES
rep = 'stdinchi'    # the desired output is StdInChI
rep = 'iupac_name'  # the desired output is IUPAC name
rep = 'cas'         # the desired output is CAS Registry Number
rep = 'formula'     # the desired output is Chemical Formula
!!! also see in https://cactus.nci.nih.gov/chemical/structure_documentation
"""
url = opsin.format(ide, rep)
response = requests.get(url)
response.raise_for_status()
print(response.text)  # InChIKey=HSFWRNGVRCDJHI-UHFFFAOYSA-N
```

### 2. OPSIN web service
主页：(https://opsin.ch.cam.ac.uk/)，
由剑桥大学分子信息学中心维护，这个网站可以将IUPAC命名转换为多种化学标识符，使用教程详见(https://opsin.ch.cam.ac.uk/instructions.html)。

**通过python的网络请求(request):**
```python
import json
import requests

opsin = 'https://opsin.ch.cam.ac.uk/opsin/{0}.{1}'
iupac_name = 'Acetylene'
ext = 'json'
reps = ('smiles', 'stdinchikey')
url = opsin.format(iupac_name, ext)
response = requests.get(url)
response.raise_for_status()
representation = json.loads(response.text)
for rep in reps:
    print(rep + ': ' + representation[rep])
```

### 3. 其它
如[NIST Chemistry WebBook](https://webbook.nist.gov/chemistry/)等。

## 二、化学信息学相关的软件包(software/toolkit related to Cheminformatics)
### 1. rdkit
```python
import rdkit
# https://www.rdkit.org/docs/source/rdkit.Chem.inchi.html
mol = rdkit.Chem.MolFromSmiles(smiles)
# input molecule and return the standard InChI string
rdkit.Chem.inchi.MolToInchi(mol, options='', logLevel=None, treatWarningAsError=False)
# input molecule and return the standard InChI key
rdkit.Chem.inchi.MolToInchiKey(mol, options='')
```

### 2. openbabel
Open Babel 基本用法[中文教程](https://zhuanlan.zhihu.com/p/40577681)或[官方手册](https://openbabel.org/docs/dev/FileFormats/Common_cheminformatics_Formats.html)。

for StdInChIKey: (https://openbabel.org/docs/dev/FileFormats/InChIKey.html)
```python
obabel -:CC(=O)Cl -oinchi     # InChI=1S/C2H3ClO/c1-2(3)4/h1H3
obabel -:CC(=O)Cl -oinchikey  # WETWJCDKMRHUPV-UHFFFAOYSA-N
```
### 3. 其它
详见(https://zhuanlan.zhihu.com/p/74540059)或相关文献。