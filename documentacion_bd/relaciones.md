
# bd relacion 1:1

# CREATE TABLE usuario (
#     id INTEGER PRIMARY KEY,
#     nombre TEXT
# );

# CREATE TABLE perfil (
#     id INTEGER PRIMARY KEY,
#     usuario_id INTEGER UNIQUE,
#     bio TEXT,
#     FOREIGN KEY(usuario_id) REFERENCES usuario(id)
# )

# relacion 1:n
# CREATE TABLE autor (
#     id INTEGER PRIMARY KEY,
#     nombre TEXT
# );

# CREATE TABLE libro (
#     id INTEGER PRIMARY KEY,
#     titulo TEXT,
#     autor_id INTEGER,
#     FOREIGN KEY (autor_id) REFERENCES autor(id)
# )


# relacion N:N
# CREATE TABLE categoria (
#     id INTEGER PRIMARY KEY,
#     nombre TEXT
# );

# CREATE TABLE libro (
#     id INTEGER PRIMARY KEY,
#     titulo TEXT
# );

# CREATE TABLE libro_categoria (
#     libro_id INTEGER,
#     categoria_id INTEGER,
#     FOREIGN KEY (libro_id) REFERENCES libro(id),
#     FOREIGN KEY (categoria_id) REFERENCES categoria(id)
# )

