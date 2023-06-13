Please adhere to my style guide:

- Use 2 spaces for indentation, put a vim modeline at the bottom to enforce it
- Use "#!/usr/bin/env bash" as the shebang
- Make sure the script always passes shellcheck
- Avoid useless echos: `echo foo | bar` should be `bar <<< "foo"`
- Avoid using getopts, I prefer a simple while loop over the args
- Use functions as much as possible, and never `exit` from a function. 
They should all use `return`, only the main block should contain `exit` 
statements.
- Include error-handling
- Error messages should be printed to stderr
- `exit 2` when the script was called without some required parameters.
- Add a usage function that get output for stderr when the script is invoked 
with invalid arguments, or no arguments all all, or with `--help` or `-h`. It 
should be the very first function in the script.
- Wrap the "main" code as follows:

```
if [[ "${BASH_SOURCE[0]}" == "${0}" ]]
then
  MAIN_FUNCTION
fi
```

- Put every statement on their own line (esp. "then" and "do"). So, instead of:

```
if xxx; then
  :
fi

while yyy; do
  :
done
```

Write:

```
if xxx
then
  :
fi

while yyy
do
  :
done
```
