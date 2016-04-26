# Types.py file is special

Turns out if you create one in you `PYTHONPATH` python will stop working.
Diagnosing the issue wasn't very easy. types.py contains names for built-in
types and by overriding such file one is entering a world of pain...
