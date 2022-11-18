# Notas de 'Good Research Code Handbook'

## Configuración del proyecto
1. Seleccionar un nombre y crear una carpeta principal (1 proyecto=  1 carpeta)
2. Inicializar repositorio en Git y sincronzar en Github
3. Configurar un ambiente virtual de trabajo
4. Crear un esqueleto de directorios
5. Instalar un gestor de paquetes


## 4. Esqueleto de directorios
### Propuesta - jupyter notebooks
- data # Backed up outside of version control
- deliver # Final polished Notebooks for consumption
- develop # Lab Notebooks stored here
- figures # Figures stored here
- src # Scripts/modules stored here

### Propuesta modulo
- data: Where you put raw data for your project. You sync if < 10 MBs
- docs: Where you put documentation, including Markdown and reStructuredText (reST). Calling it docs makes
it easy to publish documentation online through Github pages.
- results: Where you put results, including checkpoints, hdf5 files, pickle files, as well as figures and tables. 
- scripts: Where you put scripts - Python and bash alike - as well as .ipynb notebooks.
- src: Where you put reusable Python modules for your project. This is the kind of python code that you import.
- tests: Where you put tests for your code. We’ll cover testing in a later lesson.  
.gitignore  
environment.yml  
README.md  

## Recomendaciones en el uso de jupyter notebooks

### Nombre de notebooks
[ISO 8601 date]-[DS-initials]-[2-4 word description].ipynb  
2015-07-13-jw-coal-yearly-productivity.ipynb

## Recomendaciones Github

### Create a new repository on the command line

echo "# good-practice-coding" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:jondq/good-practice-coding.git
git push -u origin main

### or push an existing repository from the command line

git remote add origin git@github.com:jondq/good-practice-coding.git
git branch -M main
git push -u origin main

- Each Data Scientist has their own dev branch
- Work is saved and pushed on dev branch daily
-  When ready to merge to master, pull request
- And, finally... commit for each notebook:
  - `.ipynb`
  - `.py`
  - `.html` 
  - and figures



## Referencias

https://github.com/jbwhit/OSCON-2015