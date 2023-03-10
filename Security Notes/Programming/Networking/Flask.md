Flask hello world
```python
from flask import Flask

app = Flask(__name__)

@app.route("/")
def index():
	return "<h1>Hello flask</h1>"

if __name__ == "__main__":
	app.run(debug=True)
```

Decorators are used above functions to specify routes. Example is the index function executes when the route "/" is visited.

#flask #networking #python #servers