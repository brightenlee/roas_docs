# OnGround Robotics Tutorial

This is the source for OnGround Robotics Tutorial.

Publishing sphinx-generated docs on github
------------------------------------------

#####Set up sphinx:
```
sudo pip install sphinx
mkdir docs
cd docs
sphinx-quickstart
```

#####Set up docs repository:
```
rm -rf _build/html
cd _build
git clone https://github.com/brightenlee/docs.git html
cd html
git branch gh-pages
git symbolic-ref HEAD refs/heads/gh-pages
rm .git/index
git clean -fdx
```

#####Initial creation and commit:
```
cd _build/html
git add .
git commit -m "Initial commit"
git push origin gh-pages
```
