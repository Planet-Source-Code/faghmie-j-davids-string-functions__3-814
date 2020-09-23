<div align="center">

## String Functions


</div>

### Description

This header file contains functions to: Return the n number of characters from the left/right of a character string, remove trailing and leading spaces and replace a character with a string that is specified. The functions are pretty straight forward.
 
### More Info
 
Each function returns a pointer to the return string

None that I know of.


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Faghmie J Davids](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/faghmie-j-davids.md)
**Level**          |Intermediate
**User Rating**    |5.0 (10 globes from 2 users)
**Compatibility**  |C, C\+\+ \(general\), Microsoft Visual C\+\+, Borland C\+\+
**Category**       |[Strings](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/strings__3-26.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/faghmie-j-davids-string-functions__3-814/archive/master.zip)

### API Declarations

string.h, math.h


### Source Code

```
#include <string.h>
#include <math.h>
char * strLeft(char * str,int n)
{
	char * tmp;
	tmp = strdup(str);
	strncpy(tmp + n,"",abs(strlen(tmp) - n));
	return tmp;
}
char * strRight(char * str, int n)
{
	char * tmp;
	tmp = strdup(str);
	strrev(tmp);
	strncpy(tmp + n,"",strlen(tmp) - n);
	strrev(tmp);
	return tmp;
}
char * strTrim(char * str)
{
	char * tmp;
	tmp = strdup(str);
	//REMOVE LEADING SPACES
	while (strcmp(strLeft(tmp,1)," ") == 0)
	{
		tmp = strRight(tmp,strlen(tmp) - 1);
	}
	//REMOVE TRAILING SPACES
	while (strcmp(strRight(tmp,1)," ") == 0)
	{
		tmp = strLeft(tmp,strlen(tmp) - 1);
	}
	return tmp;
}
char * strReplace(char * str,char FindX, char * ReplaceX)
{
	char * tmp, * tmp2, * tmp3;
	tmp = strdup(str);
	tmp2 = strchr(tmp,FindX);
	while (tmp2 != NULL)
	{
		tmp3 = strLeft(tmp,strlen(tmp)-strlen(tmp2));
		tmp2++;
		tmp = strdup(tmp3);
		strcat(tmp,ReplaceX);
		strcat(tmp,tmp2);
		tmp2 = strchr(tmp,FindX);
	}
	return tmp;
}
```

