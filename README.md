# TOON Format



**TOON** (Token-Oriented Object Notation) is a compact format for sending structured data to LLMs. It cuts token usage by **30–60%** compared to JSON.



## The Problem



JSON is verbose. Every key name, quote, and bracket becomes a token your LLM must process:



```json

{

  "users": [

    {"id": 1, "name": "Alice", "role": "admin"},

    {"id": 2, "name": "Bob", "role": "user"}

  ]

}

```



## The Solution



TOON declares fields once, then just sends data:



```

users[2]{id,name,role}:

1,Alice,admin

2,Bob,user

```



**Same data. 40% fewer tokens. Lower cost.**



---



## Quick Math



For 10,000 LLM queries per day with 4,000 tokens of context:



| Format | Daily Cost | Annual Cost |

|--------|-----------|-------------|

| JSON   | $400      | $120,000   |

| TOON   | $240      | $72,000    |

| **Save** | **$160** | **$48,000** |



---



## Try It Now



👉 **[toonformat.dev/playground](https://toonformat.dev/playground)**



Paste any JSON, see TOON format. No signup, no setup.



---



## Use in Code



### Python

```bash

pip install python-toon

```

```python

from toon import encode



data = [

    {"id": 1, "name": "Alice"},

    {"id": 2, "name": "Bob"},

]

toon_str = encode(data)

print(toon_str)

# [2]{id,name}:

# 1,Alice

# 2,Bob

```



### JavaScript

```bash

npm install toon

```

```javascript

import { encode } from 'toon';



const toonStr = encode(data);

console.log(toonStr);

```



---



## When to Use



✅ LLM prompts  

✅ Uniform data (users, records, lists)  

✅ Cost-sensitive applications  



❌ APIs or databases  

❌ Deeply nested structures  

❌ Configuration files



---



## Links



- **Playground:** https://toonformat.dev/playground

- **Spec:** https://github.com/toon-format/spec

- **SDKs:** https://github.com/toon-format (TypeScript, Python, Go, Rust, PHP, etc.)



---



Made for builders who care about LLM costs and latency.
