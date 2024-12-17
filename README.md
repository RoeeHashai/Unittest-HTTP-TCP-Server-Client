
## Test for HTTP/TCP Server-Client Interaction

### Overview
This test is designed to validate the behavior of the server handling file and image requests. Each test verifies different aspects of server functionality, including response correctness for existing and non-existing files, redirection handling, and the server's ability to handle multiple consecutive requests.

### Running the Server
Before running the tests, manually start the server on port 8000 using the following command:

```bash
python3 server.py 8000
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
- **Test 7:** Assesses the server's handling of timeout scenarios, ensuring that the server remains responsive after idle periods.

### Expected Test Output
Successful execution of all tests should produce the following output:

```
$ python3 test.py
.......
----------------------------------------------------------------------
Ran 7 tests in 3.087s

OK
```

### Notes
- **Wireshark Capture:** It is recommended to run these tests in parallel with a Wireshark capture to verify the expected behaviors of connection and data transmission.
- **File and Directory Requirements:** Ensure that all necessary files and directories referenced in the tests (e.g., `files/`) are present within the project folder. Simply add the test script to your project directory and execute it from there.
- **Cross-Platform Considerations:** Differences between operating systems (Linux, Windows) may necessitate adjustments to the Python command (`python3` vs. `python`) and the paths used within the tests.
