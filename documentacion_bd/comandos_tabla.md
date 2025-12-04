# Base de datos Sqlite3
import sqlite3

#SQLite no permite eliminar columnas directamente, ni cambiar su tipo (INTEGER → TEXT) Solo permite agregar columnas al final y renombrar columnas
# tipos de datos existentes en sqlite
# INTEGER//	int//	edad, id, cantidad
# REAL//	float//	precio, temperatura
# TEXT//	str//	nombre, email
# BLOB//	binary//	imágenes, archivos binarios
# NUMERIC//	decimal, booleanos//	fechas, 0/1, True/False

# Crear conexión (si no existe una base de datos con ese nombre la creamos 
def crear_bd():
    conexion = sqlite3.connect("mi_biblioteca.db")
    conexion.commit()
    conexion.close()


# eliminamos la bd 
import os
# Nombre del archivo de base de datos
archivo_db = "mi_biblioteca.db"

if os.path.exists(archivo_db):
    os.remove(archivo_db)
    print("Base de datos eliminada.")
else:
    print("La base de datos no existe.")



def crear_tablas():
    # siempre al crear tenemos que establecer y abrir conexion con nuestra bd 
    conexion = sqlite3.connect("mi_biblioteca.db")
    cursor = conexion.cursor()
    cursor.execute("""
    CREATE TABLE IF NOT EXISTS libros (
        id INTEGER PRIMARY KEY AUTOINCREMENT,
        titulo TEXT NOT NULL,
        autor TEXT NOT NULL,
        precio REAL NOT NULL
    )
    """)

    conexion.commit()
    conexion.close()
# connect(...): crea o abre el archivo de base de datos
# cursor(): es como un lápiz que escribe en la base
# CREATE TABLE: definimos la estructura de la tabla
# REAL: número decimal (como float en Python)
# NOT NULL: campo obligatorio
# commit(): guarda los cambios
# close(): cierra la conexion


# eliminar tabla si existe 
# conectamos y ponemos en ejcucion la sentencia eliminamos la tabla si existe 
conexion = sqlite3.connect("mi_biblioteca.db")
cursor = conexion.cursor()
cursor.execute("DROP TABLE IF EXISTS libros")

conexion.commit()
conexion.close()


# ver tablas existentes 
conn = sqlite3.connect("mi_biblioteca.db")
cursor = conn.cursor()

cursor.execute("SELECT name FROM sqlite_master WHERE type='table';")
tablas = cursor.fetchall()
for tabla in tablas:
    print(tabla)

conn.close()


# cambiar el nombre de una columna 
# conectamos decimos de que tabla que columna y el nuevo nombre 
conexion = sqlite3.connect("mi_biblioteca.db")
cursor = conexion.cursor()
cursor.execute("ALTER TABLE libros RENAME COLUMN titulo TO nombre_libro;")

conexion.commit()
conexion.close()


# agregamos nueva columna en nuestra bd 
conexion = sqlite3.connect("mi_biblioteca.db")
cursor = conexion.cursor()
cursor.execute("ALTER TABLE libros ADD COLUMN editorial TEXT")

conexion.commit()
conexion.close()
