# bin2hex

- hex文件8bit对齐
`hexdump -v -e/'1 "%02x\n"'  hello > hello.hex`

- hex文件32bit对齐
`hexdump -v -e'/4 "%08x\n"'  hello > hello.hex`
