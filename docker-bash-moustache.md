# Template Mustache for bash in docker

See [Mustache for bash](https://github.com/tests-always-included/mo) repository to have explanation

Mo is a mustache template rendering software written in bash.  It inserts
environment variables into templates.

Simply put, mo will change {{VARIABLE}} into the value of that
environment variable.  You can use {{#VARIABLE}}content{{/VARIABLE}} to
conditionally display content or iterate over the values of an array.

Learn more about mustache templates at https://mustache.github.io/


# Usage

To use Docker container:

```bash
$ echo "Hello {{You}}" | docker run --rm -it -e YOU=Superman metal3d/mo
Hello Superman
```

Remember to not use "-t" option if you want to use pipeline as above.


You may link volume with ".mo" files to use template parsing, the working directory in container is "/opt":

```
$ echo "Hello {{You}}" > template.mo
$ docker run --rm -i -e YOU=Superman -v $(pwd):/opt metal3d/mo template.mo
Hello Superman
```

