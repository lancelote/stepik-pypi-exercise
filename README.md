# stepik-pypi-exercise

This code is from Stepik [Python PyPI package publication](https://stepik.org/course/Python-PyPI-package-publication-2887) course. Solely for future references.

## Final Step

This final lesson contains instructions on how to push the package you created during this course to PyPI.

*If you want to publish this package, don't forget to change its name, as stepik_exercise is already a PyPI package.*

For this step, you will need [Twine](https://pypi.python.org/pypi/twine) to publish your package safely.

```bash
sudo apt install twine
```

First, you need to register at [PyPI](https://pypi.python.org/pypi?%3Aaction=register_form) and [PyPI](https://testpypi.python.org/pypi) test. PyPI is the main index that pip uses when you run

```bash
pip install
```

command. PyPI test is used to test that your package is successfully published and can be installed.
For convenience create ~/.pypirc file that will contain your credentials for these sites

```
[distutils]
index-servers=
    pypi
    testpypi

[testpypi]
repository = https://testpypi.python.org/pypi
username = <your user name goes here>
password = <your test password goes here>

[pypi]
username = <your user name goes here>
password = <your live password optionally goes here>
```

First lets build the package

```bash
python setup.py sdist
```

This will create dist/{package-name}-{tag}.tar.gz archive that we now can download to PyPI.

Register your package at PyPI test first

```bash
python setup.py register -r https://testpypi.python.org/pypi
```

Now we can upload it to the test server

```bash
twine upload dist/{package-name}-{tag}.tar.gz -r pypitest
```

To check your package installation you can now install it from PyPI test

```bash
pip install -i https://testpypi.python.org/pypi <package name>
```

If the installation is successful, you can now publish your package to PyPI

```bash
python setup.py register -r pypi
twine upload dist/{package-name}-{tag}.tar.gz
```

And that is it! Everyone can pip install your package now!
