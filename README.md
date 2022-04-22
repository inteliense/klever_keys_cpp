# klever_keys_cpp

The purpose for this library is to have secure system keys and initialization vectors for various encryption methods (ex: AES).

By using the HideString header file, the string is hidden in the binary code, thus keeping attackers from taking and using your keys.

Use the Java application (.jar file) included to create a new class 
and header file with a matching reference file for your use with your applications.

Execute the jar by executing the following command in the terminal or command prompt (Windows, Linux, and macOS):<br><br>
`java -jar kleverkeys-generator.jar`<br><br>
Then follow the prompts (# of keys & ivs, class name, and path) to create the 3 files automatically.

To effectively prevent someone from getting the keys by copying the library, the class file's <b>get</b> function default
return value is a random hex value. This will make any brute force attempts impossible.

The id strings in the get function of the class can be seen in the binary code, however, they are 32 bytes in order for them to look like a 256 bit key or other string and require a hash of the id when finding a matching key.

<b>Don't forget to edit the variables in the CMakeLists.txt file to build and install the library as well as installing the boost library and openssl library</b>.

To build the library with cmake run the following within the directory of the source files and HideString header:
<br>
`cmake .`<br>
`cmake --build .`

To install the library (optional) with cmake run:<br>
`cmake --install .`
