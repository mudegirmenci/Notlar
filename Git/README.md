### create a new repository on the command line ###

```
echo "# Notlar" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/mudegirmenci/Notlar.git
git push -u origin main

### push an existing repository from the command line ###

git remote add origin https://github.com/mudegirmenci/Notlar.git
git branch -M main
git push -u origin main
```

- Son aşamada password alanına **pat(personel access token)** girilecek
