# creamos un indice simple 
# CREATE INDEX idx_autor ON libros(autor_id);


# creamos un indice compuesto 
#CREATE INDEX idx_titulo_precio ON libros(titulo, precio);

# para ver los indices creados 
# PRAGMA index_list(nombre_tabla);

# para saber como estan compuestos 
#PRAGMA index_info(nombre_indice);


# eliminar el index 
# DROP INDEX nombre_indice;

# asi hacemos una busqueda del index
# cursor.execute("SELECT * FROM libros WHERE titulo = ?", ("El Principito",))
# print(cursor.fetchall())

# conexion = sqlite3.connect("base_datos.db")
# cursor = conexion.conexion()
# cursor.execute("""
# CREATE INDEX idx_precio ON libros(precio);""")
# conexion.closes()