# django-essentials-kitchen
Learning django and essentials task by task

Courses referred - [https://www.udemy.com/course/python-and-django-full-stack-web-developer-bootcamp](https://www.udemy.com/course/python-and-django-full-stack-web-developer-bootcamp)


## HTML

- [task-001 - title](html/task-001-title)
- [task-002 - heading-paragraph-bold-italics](html/task-002-heading-paragraph-bold-italics)
- [task-003 - lists](html/task-003-lists)
- [task-004 - divs-spans](html/task-004-divs-spans)
- [task-005 - image-links](task-005-image-links)
- [task-006 - assignment-leanrnings-till-now](html/task-006-assignment-leanrnings-till-now)
- [task-007 - tables](html/task-007-tables)
- [task-008 - forms](html/task-008-forms)
- [task-009 - forms-labels](html/task-009-form-labels)
- [task-010 - forms-selections](html/task-010-form-selections)
- [task-011 - assignment-learnings-till-now](html/task-011-assignment-learnings-till-now)

## CSS

- [task-001 - linking-css-modify-tag-properties-h1-li-p-h4](css-html/task-001-linking-css-modify-tag-properties-h1-li-p-h4)
- [task-002 - body-div-p-span](css-html/task-002-body-div-p-span)
- [task-003 - class-id-all-siblings-descendants-attributes](css-html/task-003-class-id-all-siblings-descendants-attributes)
- [task-004 - specificity-precedence](css-html/task-004-specificity-precedence)
- [task-005 - learning-till-now-assignment](css-html/task-005-learning-till-now-assignment)
- [task-006 - fonts](css-html/task-006-fonts)
- [task-007 - box-modules-assignment](css-html/task-007-box-models-assignment)
- [task-008 - spectrum-assignment](css-html/task-008-spectrum-assignment)
- [task-009 - login-page-assignment](css-html/task-009-login-page-assignment)
 


## Bootstrap

[Bootstrap](https://getbootstrap.com)

- [task-001 - buttons](bootstrap/task-001-buttons)
- [task-002 - forms](bootstrap/task-002-forms)
- [task-003 - navbar](bootstrap/task-003-navbars)
- [task-004 - grids](bootstrap/task-004-grids)
- [task-005 - learning-assignment](bootstrap/task-005-learning-assignment)


## Javascript

- [task-001 - hello-world](javascript/task-001-hello-world)
- [task-002 - comments](javascript/task-002-comments)
- [task-003 - data-types](javascript/task-003-data-types)
- [task-004 - operations-on-datatype](javascript/task-004-operations-on-datatypes)
- [task-005 - connecting-javascript-html](javascript/task-005-connecting-javascript-html)
- [task-006 - operators](javascript/task-006-operators)
- [task-007 - control-flow](javascript/task-007-control-flow)
- [task-008 - loops](javascript/task-008-loops)
- [task-009 - functions](javascript/task-009-functions)
- [task-010 - arrays](javascript/task-010-arrays)
- [task-011 - objects](javascript/task-011-objects)


## Document Object Model

- [task-001 - change-color-heading-randomly](document-object-model/task-001-change-color-heading-randomly)
- [task-002 - two-content-interation](document-object-model/task-002-two-content-interation)
- [task-003 - events](document-object-model/task-003-events)


## jQuery

[https://code.jquery.com](https://code.jquery.com/)

[https://jquery.com](https://jquery.com/)

- [task-001 - loading-and-basics](jQuery/task-001-loading-and-basics)
- [task-002 - events](jQuery/task-002-events)


## Python

- [task-001 - numbers](python/task-001-numbers)
- [task-002 - strings](python/task-002-strings)
- [task-003 - lists](python/task-003-lists)
- [task-004 - dictionaries](python/task-004-dictionaries)
- [task-005 - tuples-sets-booleans](python/task-005-tuples-sets-booleans)
- [task-006 - control-flow](python/task-006-control-flow)
- [task-007 - functions](python/task-007-functions)
- [task-008 - modules-and-packages](python/task-008-modules-and-packages)
- [task-009 - name-and-main](python/task-009-name-and-main)
- [task-010 - scope](python/task-010-scope)
- [task-011 - object-oriented-programming](python/task-011-object-oriented-programming)
- [task-012 - errors-and-exceptions](python/task-012-errors-and-exceptions)
- [task-013 - decorators](python/task-013-decorators)
- [task-014-regular-expressions](python/task-014-regular-expressions)

## Django

[python3-virtualenv-django-project](https://medium.com/@shishirthedev/install-python3-virtualenv-django-and-start-a-new-porject-on-you-macos-de429ad3fbc0)

Installing virtual environment on mac [install-virtualenv-and-virtualenvwrapper-on-macos](https://stackoverflow.com/questions/49470367/install-virtualenv-and-virtualenvwrapper-on-macos)

###  Setting up virtual environment
```bash
$ pip3 install virtualenv virtualenvwrapper
$ mkdir Django; cd Django;
$ virtualenv django-virtual-env -p python3
$ ls django-virtual-env 
bin        lib        pyvenv.cfg
$ source django-virtual-env/bin/activate
(django-virtual-env) $ 
(django-virtual-env) $ which python3
$PWD/env_blog/bin/python3
(django-virtual-env) $ deactivate
$
```

### pip dependencies required
```bash
pip install django
pip install Faker
```

### Setting up intellij for your project

- Configure Python interpreter
  - File -> Project Structure -> SDKs -> + -> Add Python SDK -> Virtual Environment -> Existing Environment
    -> (Set the interpretter to absolute path) ./django-virtual-env/bin/python
    
- Configure the project to be able to import the python modules
  - [Right-click on project_dir -> Mark Directory as -> Sources Root](https://stackoverflow.com/questions/38342618/pycharm-not-recognizing-django-project-imports-from-my-app-models-import-thing)   

### Task List

- [task-001 - first-project](Django/task-001-first-project)
- [task-002-first-application](Django/task-002-first-application)
- [task-003 - mapping-urls](Django/task-003-mapping-urls)
- [task-004 - templates](Django/task-004-templates)
- [task-005 - static-files](Django/task-005-static-files)
- [task-006 - models](Django/task-006-models)
- [task-007 - fake-data-population](Django/task-007-fake-data-population)
- [task-008 - models-templates-views-paradigm](Django/task-008-models-templates-views-paradigm)
- [task-009 - assignment-ProdTwo](Django/task-009-assignment-ProdTwo)
- [task-010 - form-basics](Django/task-010-form-basics)
- [task-011 - relative-urls](Django/task-011-relative-urls-template-inheritence)
