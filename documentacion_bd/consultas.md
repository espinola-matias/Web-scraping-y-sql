# juntar dos tablas y traer titulo y autor 

# SELECT libro.titulo, autor.nombre
# FROM libro
# JOIN autor ON libro.autor_id = autor.id;


#filtar resultados 
# SELECT * FROM libro WHERE precio > 50;

# buscar textos parciales 
# SELECT * FROM libro WHERE titulo LIKE '%Harry%';

# hacer un orden 
# SELECT * FROM libro ORDER BY precio DESC;

# agrupar resultados 
# SELECT autor_id, COUNT(*) AS cantidad_libros
# FROM libro
# GROUP BY autor_id;

# saber datos especificos de las tablaas 
# SELECT categoria.nombre
# FROM categoria
# JOIN libro_categoria ON categoria.id = libro_categoria.categoria_id
# WHERE libro_categoria.libro_id = 3;

# todas las peticiones debemos de hacer de esta manera estructurada 
import sqlite3

conn = sqlite3.connect("mi_biblioteca.db")
cursor = conn.cursor()

cursor.execute("""
    SELECT libro.titulo, autor.nombre
    FROM libro
    JOIN autor ON libro.autor_id = autor.id;
""")

resultados = cursor.fetchall()

for fila in resultados:
    print(f"Título: {fila[0]} | Autor: {fila[1]}")

conn.close()
