# scriptexcel
unir archivos de excel

import os
import pandas as pd

# Ruta de la carpeta que contiene los archivos Excel en el escritorio
carpeta = r"C:\Users\fmora\Desktop\s"

# Lista para almacenar los marcos de datos de cada archivo Excel
frames = []


for archivo in os.listdir(carpeta):
    if archivo.endswith(".xlsx"):  # Asegurarse de que solo estamos trabajando con archivos Excel
        ruta_completa = os.path.join(carpeta, archivo)
        # Leer la hoja 1 del archivo Excel y seleccionar las columnas requeridas
        df = pd.read_excel(ruta_completa, sheet_name=0, usecols=["N°", "FECHA_RECEPCION", "SERIE", "ID_CONTRATO", "SEDE_RECEPCION"])
        
        frames.append(df)

resultado_final = pd.concat(frames, ignore_index=True)

resultado_final.to_excel(os.path.join(carpeta, "resultado_final.xlsx"), index=False)

print("Proceso completado. Se ha creado el archivo 'resultado_final.xlsx'.")


