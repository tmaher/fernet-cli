fernet-cli
==========

Now, the power of [Fernet](https://github.com/fernet/spec) is
available from the shell!

## tl;dr

```
tmaher@og-kush:~$ gem install fernet-cli
Fetching: fernet-cli-0.6.gem (100%)
Successfully installed fernet-cli-0.6
Parsing documentation for fernet-cli-0.6
Installing ri documentation for fernet-cli-0.6
Done installing documentation for fernet-cli after 0 seconds
1 gem installed
tmaher@og-kush:~$ fernet-encrypt --help
Usage: fernet-encrypt [-p | -k <keyfile>] -i <infile> -o <outfile>
    -p, --prompt                     Prompt for keys
    -k, --keyfile KEYFILE
    -i, --infile INPUTFILE
    -o, --outfile OUTPUTFILE
```

And there's a corresponding `fernet-decrypt` too.  The key should be a
base64-encoded blob of 256, 384 or 512 bits depending on the strength
of AES encryption you wish to use.  If you'd rather not write it out to
a file or get promted for it, you can save it to shell environment
variable `FERNET_CLI_KEY`.

For `fernet-encrypt`, the infile is plaintext and the outfile is
ciphertext.  For `fernet-decrypt`, the infile is ciphertext and the
outfile is plaintext.  

For more information, see https://github.com/fernet/spec

## WARNING
These helpers support the convention of specifying `-` for a filename
to mean stdin/stdout.  However, the Ruby implementation of Fernet
currently has to read the complete message into memory before
encrypting/decrypting.  If you're planning on using this in any
vaguely complicated shell pipeline, your computer's memory usage will
assplode. 
