import sqlite3

# insertamos datos nuevos a una base de datos 
def insertar_datos():
    conn = sqlite3.connect("mi_biblioteca.db")
    cursor = conn.cursor()
    cursor.execute(
        "INSERT INTO libros (titulo, autor, precio) VALUES (?, ?, ?)",
        ("El Principito", "Antoine de Saint-Exupéry", 49.90)
    )
    conn.commit()
    conn.close()



# actualizar datos de db siempre siempre especificar el campo a actualizar 
conn = sqlite3.connect("mi_biblioteca.db")
cursor = conn.cursor()
cursor.execute(
    "UPDATE libros SET precio = ? WHERE id_libro = ?",
    (59.99, "1")
)

conn.commit()
conn.close()

#ta,mbien podemos actualizar varios datos 
conn = sqlite3.connect("mi_biblioteca.db")
cursor = conn.cursor()
cursor.execute(
    "UPDATE libros SET precio = ?, calificacion = ? WHERE id_libro = ?",
    (59.99, "cinco", 1)
)

conn.commit()
conn.close()

#eliminamos datos de una base de datos
cursor.execute("DELETE FROM libros WHERE id = ?", (1,))
