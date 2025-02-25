pysenseword

A module for detecting sensitive words in text using different algorithms.

Available algorithms:
- DFA (Deterministic Finite Automaton)
- Aho-Corasick algorithm
- Regular expression
- String find

Example usage:


DFA:
```python
from pysenseword import search

text = "This is a test text without a sensitivetest word."
results = search(text, method='dfa')
print(results)
```

Output:

```
{'find': True, 'word': 'sensivetest', 'dict': {'line': 7348, 'index': 30}}
```
or
```
{'find': False, 'word': '', 'dict': {'line': 0, 'index': 0}}
```

Other algorithms:

```python
from pysenseword import search

text = "This is a test text without a sensitivetest word."
results = search(text, method='ac')
print(results)
```

Output:

```
{'find': True, 'words': {('sensitivetest', 30)}}
```
or
```
{'find': False, 'words': set()}
```

```python
from pysenseword import search

text = "This is a test text without a sensitivetest word."
results = search(text, method='re')
print(results)
```

Output:

```
{'find': True, 'words': {('sensitivetest', 30)}}
```

```python
from pysenseword import search

text = "This is a test text without a sensitivetest word."
results = search(text, method='str')
print(results)
```

Output:

```

The `search` function takes three arguments:
- `text`: the text to search for sensitive words
- `method`: the algorithm to use for detecting sensitive words. Available options are:
  - `dfa`: DFA algorithm
  - `ac`: Aho-Corasick algorithm
  - `re`: Regular expression
  - `str`: String find

Advanced usage:

You can customize the algorithm by passing additional arguments to the `search_advanced` function.

```search_advanced(text,method='dfa',dictionary='default',method_function=None, run_before=None, run_after=None):```
text: the text to search for sensitive words
method: the algorithm to use for detecting sensitive words. Usage is same as in `search` function.
dictionary: the dictionary to use for detecting sensitive words. Usage is same as in `search` function.
method_function: a function that takes the text and returns a list of sensitive words. If not provided, the default function is used.
run_before: a function that takes the text and returns the modified text before running the algorithm. If not provided, the default function is used.
run_after: a function that takes the text and the result of the algorithm and returns the modified result. If not provided, the default function is used.

Example usage:

```python
from pysenseword import search_advanced

text = "This is a test text without a sensitivetest word."
results = search_advanced(text, method='dfa', dictionary='default', method_function=None, run_before=None, run_after=None)
print(results)
```

Output:

```
{'find': True, 'word': 'sensivetest', 'dict': {'line': 7348, 'index': 30}}
