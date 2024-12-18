
## Test for HTTP/TCP Server-Client Interaction

### Overview
This test is designed to validate the behavior of the server handling file and image requests. Each test verifies different aspects of server functionality, including response correctness for existing and non-existing files, redirection handling, and the server's ability to handle multiple consecutive requests.

### Running the Server
Before running the tests, manually start the server on port 80 using the following command:

```bash
python3 server.py 80
```

If you wish to use a different port, ensure to update the port number in the test scripts as well.

### Running the Tests
To execute the tests, use the following command:

```bash
python3 test.py
```

### Test Descriptions
- **Test 1:** Validates that an existing HTML file (`/index.html`) can be retrieved successfully.
- **Test 2:** Checks the server's response when a non-existing file is requested, expecting a 404 Not Found.
- **Test 3:** Tests server redirection handling, ensuring the server redirects correctly and serves the target file.
- **Test 4:** Confirms the server can handle multiple different file requests in succession and that each file is served correctly.
- **Test 5:** Specifically tests the retrieval of image files, verifying that the images are received correctly and match expected contents.
- **Test 6:** Sends invalid requests to the server, expecting a 404 Not Found response for each.
- **Test 7:** Assesses the server's handling of timeout scenarios, ensuring that the server closes the client connection if there is no traffic on a socket for 1 second. Note: This test is not relevant for implementations where the client does not maintain a keep-alive connection. If your client closes the connection after each request, the server will naturally close the connection, and therefore, the timeout behavior will not be tested effectively.
- **Test 8:** Verifies the server's ability to handle alternating requests for image and text files in a sequential manner.

### Expected Test Output
Successful execution of all tests should produce the following output:

```
$ python3 test.py
........
----------------------------------------------------------------------
Ran 8 tests in 3.087s

OK
```

### Notes
- **Wireshark Capture:** It is recommended to run these tests in parallel with a Wireshark capture to verify the expected behaviors of connection and data transmission.
- **File and Directory Requirements:** Ensure that all necessary files and directories referenced in the tests (e.g., `files/`) are present within the project folder. Simply add the test script to your project directory and execute it from there.
- **Log File:** The test generates a log file that records all commands sent to the client and all responses printed to the client's stdout. This can be useful for troubleshooting and verifying test outcomes.
- **Cross-Platform Considerations:** Differences between operating systems (Linux, Windows) may necessitate adjustments to the Python command (`python3` vs. `python`) and the paths used within the tests.
