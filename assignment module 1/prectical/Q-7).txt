from http.server import BaseHTTPRequestHandler, HTTPServer

class SimpleHandler(BaseHTTPRequestHandler):
    def do_GET(self):
        self.send_response(200)
        self.send_header('Content-type', 'text/html')
        self.end_headers()
        message = "<html><body><h1>Hello from Server!</h1></body></html>"
        self.wfile.write(message.encode())

if __name__ == "__main__":
    server_address = ('localhost', 8080)
    httpd = HTTPServer(server_address, SimpleHandler)
    print("Starting server on http://localhost:8080...")
    httpd.serve_forever()
