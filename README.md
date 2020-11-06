Sample app that reproduces https://github.com/microsoft/vscode-python/issues/14579 - see [comment](https://github.com/microsoft/vscode-python/issues/14579#issuecomment-723284293)

Here is a screenshot showing the errors I see when using `2020.10.332292344`
- `pylint` is failing on line 3: `from awesome_pkg import thing_doer`
- `pytest` is failing on the same import line: `E   ModuleNotFoundError: No module named 'awesome_pkg'`

![image](https://user-images.githubusercontent.com/227505/98411448-f93d4b80-206d-11eb-977f-0f0c45af8759.png)

Output from the `Output` > `Python` panel is as follows:

```
----------Generating Tags----------
ctags --options=/Users/dlaing/.vscode/extensions/ms-python.python-2020.10.332292344/resources/ctagOptions --languages=Python --exclude=**/site-packages/** -o /Users/dlaing/workspace/vscode-python-issue14579-example/.vscode/tags .
> ctags --options=/Users/dlaing/.vscode/extensions/ms-python.python-2020.10.332292344/resources/ctagOptions --languages=Python --exclude=**/site-packages/** -o ~/workspace/vscode-python-issue14579-example/.vscode/tags .
cwd: ~/workspace/vscode-python-issue14579-example
ctags: Warning: --extra option is obsolete; use --extras instead
> ~/.local/share/virtualenvs/vscode-python-issue14579-example-j6G2tqz-/bin/python ~/.vscode/extensions/ms-python.python-2020.10.332292344/pythonFiles/pyvsc-run-isolated.py pylint --disable=all --enable=F,unreachable,duplicate-key,unnecessary-semicolon,global-variable-not-assigned,unused-variable,unused-wildcard-import,binary-op-exception,bad-format-string,anomalous-backslash-in-string,bad-open-mode,E0001,E0011,E0012,E0100,E0101,E0102,E0103,E0104,E0105,E0107,E0108,E0110,E0111,E0112,E0113,E0114,E0115,E0116,E0117,E0118,E0202,E0203,E0211,E0213,E0236,E0237,E0238,E0239,E0240,E0241,E0301,E0302,E0303,E0401,E0402,E0601,E0602,E0603,E0604,E0611,E0632,E0633,E0701,E0702,E0703,E0704,E0710,E0711,E0712,E1003,E1101,E1102,E1111,E1120,E1121,E1123,E1124,E1125,E1126,E1127,E1128,E1129,E1130,E1131,E1132,E1133,E1134,E1135,E1136,E1137,E1138,E1139,E1200,E1201,E1205,E1206,E1300,E1301,E1302,E1303,E1304,E1305,E1306,E1310,E1700,E1701 --msg-template='{line},{column},{category},{symbol}:{msg}' --reports=n --output-format=text ~/workspace/vscode-python-issue14579-example/awesome_pkg/test/test_thing_doer.py
cwd: ~/workspace/vscode-python-issue14579-example
> ~/.local/share/virtualenvs/vscode-python-issue14579-example-j6G2tqz-/bin/python ~/.vscode/extensions/ms-python.python-2020.10.332292344/pythonFiles/pyvsc-run-isolated.py pylint --disable=all --enable=F,unreachable,duplicate-key,unnecessary-semicolon,global-variable-not-assigned,unused-variable,unused-wildcard-import,binary-op-exception,bad-format-string,anomalous-backslash-in-string,bad-open-mode,E0001,E0011,E0012,E0100,E0101,E0102,E0103,E0104,E0105,E0107,E0108,E0110,E0111,E0112,E0113,E0114,E0115,E0116,E0117,E0118,E0202,E0203,E0211,E0213,E0236,E0237,E0238,E0239,E0240,E0241,E0301,E0302,E0303,E0401,E0402,E0601,E0602,E0603,E0604,E0611,E0632,E0633,E0701,E0702,E0703,E0704,E0710,E0711,E0712,E1003,E1101,E1102,E1111,E1120,E1121,E1123,E1124,E1125,E1126,E1127,E1128,E1129,E1130,E1131,E1132,E1133,E1134,E1135,E1136,E1137,E1138,E1139,E1200,E1201,E1205,E1206,E1300,E1301,E1302,E1303,E1304,E1305,E1306,E1310,E1700,E1701 --msg-template='{line},{column},{category},{symbol}:{msg}' --reports=n --output-format=text ~/workspace/vscode-python-issue14579-example/awesome_pkg/test/test_thing_doer.py
cwd: ~/workspace/vscode-python-issue14579-example
##########Linting Output - pylint##########
************* Module test_thing_doer
3,0,error,import-error:Unable to import 'awesome_pkg'

--------------------------------------------------------------------
Your code has been rated at -2.50/10 (previous run: -2.50/10, +0.00)

> ~/.local/share/virtualenvs/vscode-python-issue14579-example-j6G2tqz-/bin/python ~/.vscode/extensions/ms-python.python-2020.10.332292344/pythonFiles/testing_tools/run_adapter.py discover pytest -- --rootdir ~/workspace/vscode-python-issue14579-example -s --cache-clear -o junit_family=xunit1 .
cwd: ~/workspace/vscode-python-issue14579-example
```

And the `Python Test Log`
```
============================= test session starts ==============================
platform darwin -- Python 3.8.6, pytest-6.1.2, py-1.9.0, pluggy-0.13.1
rootdir: /Users/dlaing/workspace/vscode-python-issue14579-example
collected 1 item

awesome_pkg/test/test_syspath.py ['/Users/dlaing/workspace/vscode-python-issue14579-example/awesome_pkg/test', '/Users/dlaing/.vscode/extensions/ms-python.python-2020.10.332292344/pythonFiles', '/usr/local/opt/python@3.8/Frameworks/Python.framework/Versions/3.8/lib/python38.zip', '/usr/local/opt/python@3.8/Frameworks/Python.framework/Versions/3.8/lib/python3.8', '/usr/local/opt/python@3.8/Frameworks/Python.framework/Versions/3.8/lib/python3.8/lib-dynload', '/Users/dlaing/.local/share/virtualenvs/vscode-python-issue14579-example-j6G2tqz-/lib/python3.8/site-packages']
.

- generated xml file: /var/folders/cx/c_41bpzs1jlc465fx_k_9qfh0000gn/T/tmp-75980YJBGpPLpDxBW.xml -
============================== 1 passed in 0.02s ===============================
============================= test session starts ==============================
platform darwin -- Python 3.8.6, pytest-6.1.2, py-1.9.0, pluggy-0.13.1
rootdir: /Users/dlaing/workspace/vscode-python-issue14579-example
collected 0 items / 1 error

==================================== ERRORS ====================================
_____________ ERROR collecting awesome_pkg/test/test_thing_doer.py _____________
ImportError while importing test module '/Users/dlaing/workspace/vscode-python-issue14579-example/awesome_pkg/test/test_thing_doer.py'.
Hint: make sure your test modules/packages have valid Python names.
Traceback:
/usr/local/opt/python@3.8/Frameworks/Python.framework/Versions/3.8/lib/python3.8/importlib/__init__.py:127: in import_module
    return _bootstrap._gcd_import(name[level:], package, level)
awesome_pkg/test/test_thing_doer.py:3: in <module>
    from awesome_pkg import thing_doer
E   ModuleNotFoundError: No module named 'awesome_pkg'
- generated xml file: /var/folders/cx/c_41bpzs1jlc465fx_k_9qfh0000gn/T/tmp-75980qb4RBaZUAhyE.xml -
=========================== short test summary info ============================
ERROR awesome_pkg/test/test_thing_doer.py
!!!!!!!!!!!!!!!!!!!! Interrupted: 1 error during collection !!!!!!!!!!!!!!!!!!!!
=============================== 1 error in 0.10s ===============================
python /Users/dlaing/.vscode/extensions/ms-python.python-2020.10.332292344/pythonFiles/testing_tools/run_adapter.py discover pytest -- --rootdir /Users/dlaing/workspace/vscode-python-issue14579-example -s --cache-clear -o junit_family=xunit1 .
```

If I downgrade to `2020.9.114305` both these errors go away:

```
cwd: ~/workspace/vscode-python-issue14579-example
> ~/.local/share/virtualenvs/vscode-python-issue14579-example-j6G2tqz-/bin/python ~/.vscode/extensions/ms-python.python-2020.9.114305/pythonFiles/pyvsc-run-isolated.py pylint --disable=all --enable=F,unreachable,duplicate-key,unnecessary-semicolon,global-variable-not-assigned,unused-variable,unused-wildcard-import,binary-op-exception,bad-format-string,anomalous-backslash-in-string,bad-open-mode,E0001,E0011,E0012,E0100,E0101,E0102,E0103,E0104,E0105,E0107,E0108,E0110,E0111,E0112,E0113,E0114,E0115,E0116,E0117,E0118,E0202,E0203,E0211,E0213,E0236,E0237,E0238,E0239,E0240,E0241,E0301,E0302,E0303,E0401,E0402,E0601,E0602,E0603,E0604,E0611,E0632,E0633,E0701,E0702,E0703,E0704,E0710,E0711,E0712,E1003,E1101,E1102,E1111,E1120,E1121,E1123,E1124,E1125,E1126,E1127,E1128,E1129,E1130,E1131,E1132,E1133,E1134,E1135,E1136,E1137,E1138,E1139,E1200,E1201,E1205,E1206,E1300,E1301,E1302,E1303,E1304,E1305,E1306,E1310,E1700,E1701 --msg-template='{line},{column},{category},{symbol}:{msg}' --reports=n --output-format=text ~/workspace/vscode-python-issue14579-example/awesome_pkg/test/test_thing_doer.py
cwd: ~/workspace/vscode-python-issue14579-example
##########Linting Output - pylint##########

--------------------------------------------------------------------
Your code has been rated at 10.00/10 (previous run: 10.00/10, +0.00)

> ~/.local/share/virtualenvs/vscode-python-issue14579-example-j6G2tqz-/bin/python ~/.vscode/extensions/ms-python.python-2020.9.114305/pythonFiles/testing_tools/run_adapter.py discover pytest -- --rootdir ~/workspace/vscode-python-issue14579-example -s --cache-clear -o junit_family=xunit1 .
cwd: ~/workspace/vscode-python-issue14579-example
```