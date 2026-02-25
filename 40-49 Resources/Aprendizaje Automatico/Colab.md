Instalar librerias en colab
``` python
!pip install cowsay
```

### Montar el drive
``` python
from google.colab import drive
drive.mount('content/drive')
```

### Subir archivos
``` python
from google.colab import files
archivo = files.upload()
```

### Descargar archivos
``` python
from google.colab import files
files.download("archivo.ext")
```