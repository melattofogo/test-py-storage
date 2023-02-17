### config/

```
mkdir test-py-storage && cd test-py-storage
```

```
mkdir config && cd config
```

```
type nul > README.md
```

### conda env

Criar o ambiente ```test-py```
```
conda create --name test-py python=3.9
```

Se as requisições para ```conda``` estão retornando ```CondaHTTPError: HTTP 000 CONNECTION FAILED``` executar ```conda config --set ssl_verify no```<sup id="lfn1">[1](#fn1)</sup>

Remover o ambiente ```test-py```
```
conda remove --name test-py --all
```

### jupyter

```
pip install jupytext --upgrade
```

```
jupyter notebook --generate-config
```

Abir o arquivo ```jupyter_notebook_config.py``` gerado em ```~\.jupyter\jupyter_notebook_config.py```

Editar o arquivo e buscar ```Ctrl``` + ```f```:
```contents_manager_class``` Adiciona e Salva:

```
#c.NotebookApp.contents_manager_class="jupytext.TextFileContentsManager"
c.ContentsManager.default_jupytext_formats = ".ipynb,.Rmd"
```

```
conda install -c conda-forge jupyter_contrib_nbextensions
```

ou

```
pip install jupyter_contrib_nbextensions
```

```
jupyter contrib nbextension install --user
jupyter nbextension enable varInspector/main
```

Se ```Validating: ok``` reabra ```jupyter notbeook```

```
jupyter nbextensions_configurator enable
```

Se a aba do ```nbextensions``` estiver visivel, mas nenhuma extensão estiver disponível:

```
pip uninstall notebook
pip install notebook==5.7.8
```

#### Data libs

```
pip install pandas
pip install pyarrow
pip install fastparquet
```

Se as requisições para ```pip``` estão retornando ```SSLError(SSLCertVerificationError(1, '[SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed: self-signed certificate in certificate chain``` executar ```python -m pip install --trusted-host files.pythonhosted.org --trusted-host pypi.org --trusted-host pypi.python.org [--proxy ...] [--user] <packagename>```<sup id="lfn2">[2](#fn2)</sup>

### git

```
git init
```

```
git add .gitignore
```

```
git commit -m "commit inicial"
```

### VSCode

```Ctrl``` + ```Shift``` + ```P```

```Python: Select Interpreter```

### Referências:

- <sub id="fn1">[1]: [https://stackoverflow.com/a/51719759/6668866](https://stackoverflow.com/a/51719759/6668866). [↩](#lfn1)</sub>
- <sub id="fn2">[2]: [https://stackoverflow.com/a/49991986/6668866](https://stackoverflow.com/a/49991986/6668866). [↩](#lfn2)</sub>