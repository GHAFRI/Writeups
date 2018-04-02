# Winners

`Reverse Me`

## Solution

We start of by checking file format with `file <name>` and we see `ELF 32-bit LSB executable`
Now lets run it by `./<name>` and we get
```
--------------------------------------------------------------------
--------------------------------------------------------------------
	        _~      
	     _~)_) _~   
	    )_))_))_)   
	    _!__!__!_   
	    \______t/  
	  ~~~~~~~~~~~~~

	 A new land is near...Let's anchor for a while...

--------------------------------------------------------------------
--------------------------------------------------------------------
```
We continue by pressing `[ENTER]` to the very end. We get some clues like 
```
ejm97

BjI7y&l~}<~-][=234af456føæ?tip=VG8gZm  
luZCB5b3VyIHRyZWFzdXJlLCBmb2xsb3cgdGh 
lIG1hcCBpbnN0cnVjdGlvbnMuLi4=

_FTW<h@c|
```
Those are not the flag, so we import to `IDA 32`.
If we look at the `main` function by pressing `F5` we see
```
int __cdecl main(int argc, const char **argv, const char **envp)
{
  cship();
  cskull();
  cmap();
  cfootsteps();
  crip();
  ckey();
  cfootsteps();
  cchest();
  inside1();
  inside2();
  puts("\n");
  return 0;
}
```
All those functions are just garbage clues except function `inside2`. 
Inside we see 
```
void inside2()
{
  _BYTE *ptr; // ST1C_4

  system("clear");
  printf("--------------------------------------------------------------------");
  printf("\n--------------------------------------------------------------------");
  ptr = malloc(0xAu);
  reveal(ptr);
  scramble((int)ptr);
  printf("\n\tI've found the map, the KEy, the chest...");
  printf("\n\t\t...Wa-wait... What's happening...");
  printf("\n\t*********************************************");
  printf("\n\t**                                         **");
  printf("\n\t**  Revealing what you're looking for...   **");
  printf("\n\t**                                         **");
  printf("\n\t**             %s                   **", ptr);
  printf("\n\t**                                         **");
  printf("\n\t*********************************************");
  putchar(10);
  printf("--------------------------------------------------------------------");
  printf("\n--------------------------------------------------------------------");
  __isoc99_scanf("%c", &hit);
  free(ptr);
}
```
which shows that function `reveal` returns the flag, however the function `scramble` destroys it. 
Therefore, all we have to do is remove `scramble` function.
To do that we switch back to the `IDA View-A` tab then we look up the `call    scramble`.
The we go to `Edit -> Patch Program -> Assemble` and change it to `nop` 5 times.
Now we need to save by `Edit -> Patch Program -> Apply Patches to input file.`
Lets run it again and we see at the end
```
--------------------------------------------------------------------
--------------------------------------------------------------------
	I've found the map, the KEy, the chest...
		...Wa-wait... What's happening...
	*********************************************
	**                                         **
	**  Revealing what you're looking for...   **
	**                                         **
	**             h@c|<_FTW                   **
	**                                         **
	*********************************************
--------------------------------------------------------------------
--------------------------------------------------------------------
```
The flag is `h@c|<_FTW`.