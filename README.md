# klever_keys_cpp

The purpose for this library is to have secure system keys and initialization vectors for various encryption methods (ex: AES).

By using the HideString header file, the string is hidden in the binary, thus keeping attackers from taking and using your keys.

Use the Java command line application (.jar file) included to create a new class 
and header file with a matching reference file for your use with your applications.

Execute the jar by executing the following command in the terminal or command prompt:<br>
`java -jar kleverkeys-generator.jar`<br>
Then follow the prompts (# of keys & ivs, class name, and path) to create the 3 files automatically.

Edit the variables in the CMakeLists.txt file to build and install the library.

To build the library with cmake run the following within the directory of the source files and HideString header:
<br>
`cmake .`<br>
`cmake --build .`

To install the library (optional) with cmake run:<br>
`cmake --install .`
