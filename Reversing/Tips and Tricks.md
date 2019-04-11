# Tips and tricks I used when solving reverso:
## CFF Explorer
Is a tool that helps in extracting data tables from an executable.

## Conversions:
### Convert from Hex file to Binary file:
`xxd -r -p input.txt output.txt`
## Scripts:

### Simple Flag Scrip #1
If you find a messy string of the flag and found a value table for it, use this script to recover it:  
```py3
data = "messy flag string"
values = [Values in 0x00]
total = ""
for x in range(len(values)):
	total += data[values[x]]
	print(total)
```

### Bruteforce elf:
A simple bruteforcer that whenever a correct followup character of the flag is given.  
(bfelf.rb)
```rb
flag = ''
until flag[-1] == '}'
  [*'A'..'Z', *'a'..'z', *'0'..'9', '_', '{', '}'].each do |ch|
    result = `./file #{flag + ch}`
    if result.include? 'flag'
      flag += ch
      puts flag
      break
    end
  end
end
puts flag
```
