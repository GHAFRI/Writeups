# Tips and tricks I used when solving reverso:
## Scripts:
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
