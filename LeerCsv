# Leer archivo CSV en Google Colab
# Gist para cargar archivos CSV de diferentes formas

import pandas as pd
from google.colab import files
import io

# OPCIÓN 1: Subir archivo desde tu computadora
print("=== OPCIÓN 1: Subir desde tu computadora ===")
# Esto abre una ventana para seleccionar el archivo
uploaded = files.upload()

# Leer el archivo subido
for filename in uploaded.keys():
    print(f'Archivo subido: {filename}')
    df = pd.read_csv(io.BytesIO(uploaded[filename]))
    print(f'Dimensiones: {df.shape}')
    print(df.head())

# OPCIÓN 2: Desde Google Drive (si tienes el archivo ahí)
print("\n=== OPCIÓN 2: Desde Google Drive ===")
from google.colab import drive
drive.mount('/content/drive')

# Cambia la ruta por la ubicación de tu archivo
# df = pd.read_csv('/content/drive/My Drive/mi_archivo.csv')
# print(df.head())

# OPCIÓN 3: Desde una URL directa
print("\n=== OPCIÓN 3: Desde URL ===")
# Ejemplo con datos de prueba
url = "https://raw.githubusercontent.com/plotly/datasets/master/iris.csv"
df_url = pd.read_csv(url)
print(f'Dataset desde URL - Dimensiones: {df_url.shape}')
print(df_url.head())

# BONUS: Función reutilizable para leer CSVs
def leer_csv_colab(metodo='upload', ruta_o_url=None):
    """
    Función para leer CSV en Colab de diferentes formas
    
    metodo: 'upload', 'drive', o 'url'
    ruta_o_url: ruta del archivo o URL (para métodos 'drive' y 'url')
    """
    
    if metodo == 'upload':
        uploaded = files.upload()
        for filename in uploaded.keys():
            return pd.read_csv(io.BytesIO(uploaded[filename]))
    
    elif metodo == 'drive':
        if ruta_o_url is None:
            print("Necesitas proporcionar la ruta del archivo en Drive")
            return None
        drive.mount('/content/drive')
        return pd.read_csv(ruta_o_url)
    
    elif metodo == 'url':
        if ruta_o_url is None:
            print("Necesitas proporcionar la URL del archivo")
            return None
        return pd.read_csv(ruta_o_url)
    
    else:
        print("Método no válido. Usa: 'upload', 'drive', o 'url'")
        return None

# Ejemplos de uso de la función:
# df = leer_csv_colab('upload')  # Para subir archivo
# df = leer_csv_colab('drive', '/content/drive/My Drive/datos.csv')  # Desde Drive
# df = leer_csv_colab('url', 'https://ejemplo.com/datos.csv')  # Desde URL
