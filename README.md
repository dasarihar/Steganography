STEGANOGRAPHY
1.main function 
  1. The program starts with the `main()` function, where it checks the operation type using the command-line arguments (`-e` for encoding or `-d` for decoding).  
  2. If encoding (`-e`) is chosen, the `read_and_validate_encode_args()` function validates the source BMP and secret text files passed as arguments.  
  3. After validation, the encoding process proceeds with `do_encoding()`.  
  4. If decoding (`-d`) is chosen, `read_and_validate_decode_args()` validates the arguments for decoding.  
  5. The `check_operation_type()` function identifies whether to perform encoding, decoding, or return an unsupported operation.  
  6. In `read_and_validate_encode_args()`, the program checks if the BMP and text files have valid extensions.  
  7. It sets the stego image filename, either by using a default name or a user-provided one.  
  8. The validated source BMP file and secret text file paths are stored in `encInfo`.  
  9. For unsupported operations, an error message is displayed.  
  10. The program handles both encoding and decoding operations based on user input.

2.do encoding
Opening Files: The program first opens the BMP image, secret file, and creates the stego image.
Capacity Check: It checks if the BMP image has enough space to hide the secret file, considering the size of the file and additional metadata.
Encoding Data:
Magic String: A magic string is encoded into the BMP to mark the presence of hidden data.
Secret File Extension: The program encodes the secret file's extension (e.g., .txt) into the BMP image.
Secret File Size: The size of the secret file is hidden within the image.
Secret File Content: Finally, the contents of the secret file are encoded into the image byte-by-byte.
Copying Remaining Data: Once encoding is complete, the program copies the remaining unaltered data from the source BMP to the stego image.
Completion: The process finishes, resulting in a BMP image that visually appears unchanged but contains hidden data.

3.do decoding  
  1. Validate the command-line arguments for the correct number and file extensions.  
  2. Open the stego BMP image file for reading, handling errors if any.  
  3. Skip the 54-byte BMP header to access the actual data.  
  4. Decode the length of the magic string from the image's least significant bits (LSBs).  
  5. Read and decode the magic string using the extracted length.  
  6. Prompt the user to enter the magic string and compare it with the decoded one.  
  7. Decode the length of the secret file extension from the LSBs.  
  8. Decode the secret file extension and append it to the output file name.  
  9. Retrieve the size of the hidden file and decode its data.  
  10. Write the decoded secret data into the output file and close the files.  
