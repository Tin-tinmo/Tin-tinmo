from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route('/')
def home():
    return jsonify({"status": "RemoteWipe API is running"})

@app.route('/wipe', methods=['POST'])
def wipe_data():
    data = request.get_json()
    email = data.get('email')
    return jsonify({"message": f"Data wipe initiated for {email}"}), 200

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=10000)
