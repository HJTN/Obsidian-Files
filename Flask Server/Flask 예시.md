```python
from flask import Flask, escape, request

app = Flask(__name__)

@app.route('/')

def hello():
    name = request.args.get("name", "World")
    return f'Hello, {escape(name)}!'

@app.route('/calculator/<string:operation>/<int:value1>/<int:value2>')
def calculator(operation, value1, value2):
    ret = 0
    if operation == "add":
        ret = value1 + value2
    elif operation == "sub":
        ret = value1 - value2
    elif operation == "mul":
        ret = value1 * value2
    elif operation == "div":
        ret = value1 / value2
    return f'Operation {operation} with {value1} and {value2} is {ret}'

@app.route('/information')
def information():
    users = [{'name' : 'John Smith', 'workplace' : 'School', 'userid' : '10011'},
            {'name' : 'U.N. Owen', 'workplace' : 'DoA', 'userid' : '10021'},
            {'name' : 'Guest', 'workplace' : 'None', 'userid' : '10001'}]

    name = request.args.get("name", "Guest")
    workplace = request.args.get("workplace", "None")  

    for user in users:
        if user['name'] == name and user['workplace'] == workplace:
            return f'Hello, {name}#{user["userid"]}!'

    return 'Who are you?'

@app.route('/input/<string:name>')
def printname(name):
    return f'Hello {name}!'

if __name__ == "__main__":
    app.run(host='127.0.0.1', port=8080)
```