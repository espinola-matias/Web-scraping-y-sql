import sqlite3

def crear_bd():
    conn = sqlite3.connect("Base_dato.db")
    conn.commit()
    conn.close()

def crear_tabla():
    conn = sqlite3.connect("Base_dato.db")
    cursor = conn.cursor()

    cursor.execute("""
    CREATE TABLE IF NOT EXISTS Libro (
        id INTEGER PRIMARY KEY AUTOINCREMENT,
        nombre TEXT NOT NULL, 
        precio INTEGER NOT NULL,
        calificacion TEXT NOT NULL, 
        descripcion TEXT NOT NULL
    )
    """)
    conn.commit()
    conn.close()

def cargar_datos(nombre, precio, calificacion, descripcion):
    conn = sqlite3.connect("Base_dato.db")
    cursor = conn.cursor()

    cursor.execute("""
    INSERT INTO Libro (nombre, precio, calificacion, descripcion)
    VALUES (?, ?, ?, ?)
    """, (nombre, precio, calificacion, descripcion))
    
    conn.commit()
    conn.close()

def insertar_datos(nombre, precio, calificacion, descripcion):
    conn = sqlite3.connect("Base_dato.db")
    cursor = conn.cursor()
    sentencias = f"INSERT INTO libro VALUES ('{nombre}', {precio}, '{calificacion}','{descripcion}')"

    cursor.execute(sentencias)
    
    conn.commit()
    conn.close()


def seleccionar_dato():
    conn = sqlite3.connect("Base_dato.db")
    cursor = conn.cursor()

    cursor.execute("SELECT * FROM Libro")
    for fila in cursor.fetchall():
        print(fila)

    conn.close()


if __name__ == "__main__":

# crear_tabla()
# cargar_datos()
# seleccionar_dato()
#cargar_datos("Mentes millonarias", 200.000, "Cuatro", "buen libro de inicio en inversiones")
    #seleccionar_dato()
    import os
    # Nombre del archivo de base de datos
    archivo_db = "Base_dato.db"

    if os.path.exists(archivo_db):
        os.remove(archivo_db)
        print("Base de datos eliminada.")
    else:
        print("La base de datos no existe.")