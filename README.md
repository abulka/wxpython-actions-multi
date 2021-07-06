# wxpython-actions-multi

An experiment re checking out not only this project, but another project, then building an exe from combining the two.

On github, If we check out this project into `mainproj` then the other project into 

- subdir/mainproj/
- relationship_manager/

The reason for `subdir` is to locate this main project relative to `relationship_manager` the way it is on my development machine.

Then from 

    mainproj/src/simple.py

we should be able to find the package

    relationship_manager/relmgr

as long as cwd when running is 

    mainproj/src/
    
and as long as the PYTHONPATH is set to

    PYTHONPATH="../../../relationship-manager/"


Yikes, a bit convoluted. Would be easier to just import `relationship_manager` as a package using pip.

# Pyinstaller

Can build this OK, as I do it locally.  Spec file needs to be

```python
a = Analysis(['src/rubber_band_async.py'],
             pathex=[
                 '../../relationship-manager/',
             ], 

```

for Pyinstaller to find everything.