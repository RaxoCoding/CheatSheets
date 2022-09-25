# pwntools

## Remote Connection

### Connect with ssh
```python
shell = ssh(USER, SERVER, password=PASS, port=PORT)
```

### Download file locally
```python
shell.download_file(FILE_PATH)
```

## I/O Streams

### Read elf file and create an ELF object
```python
elf = ELF(FILE)
```

### Start I/O proccess of an elf
```python
io = process(elf.path, stdin=PTY)
```

### Send line to process
```python
io.sendline(payload)
```

### Read line from process
```python
recieved = str(io.recvline().strip())
```

### Go interactive
```python
io.interactive()
```

## Search Techniques

### Look for a string and print its address
```python
for address in elf.search(b'/bin/bash\x00'):
    print(hex(address))
```

### Find the address of a symbol (function)
```python
targetAddr = hex(elf.symbols['shell'])
targetPkAddr = p32(elf.symbols['shell'], endian='little')
```

### 0xdeadbeef
```python
targetAddr = hex(0xdeadbeef)
targetPkAddr = p32(0xdeadbeef, endian='little')
```

## Feedback

### Print success
```python
log.success(f"Success!")
```

### Print info
```python
log.info(f"Info!")
```

### Print warning
```python
log.warning(f"Warning!")
```

### Print error
```python
log.error(f"Error!")
```
