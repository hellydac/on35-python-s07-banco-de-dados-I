CREATE TABLE estoque_filmes (
    id INTEGER PRIMARY KEY,
    filme_id INT,
    quantidade INT,
    status VARCHAR(20),
    FOREIGN KEY (filme_id) REFERENCES filmes(id)
);

SELECT * FROM estoque_filmes

INSERT INTO estoque_filmes (filme_id, quantidade, status) VALUES (1, 10, 'Disponível');
INSERT INTO estoque_filmes (filme_id, quantidade, status) VALUES (2, 5, 'Disponível');
INSERT INTO estoque_filmes (filme_id, quantidade, status) VALUES (3, 15, 'Disponível');

CREATE TABLE filmes (
    id INTEGER PRIMARY KEY,
    titulo TEXT,
    genero TEXT,
    diretor TEXT,
    ano_lancamento INTEGER,
    preco REAL
);

INSERT INTO filmes (titulo, genero, diretor, ano_lancamento, preco) VALUES ('O Poderoso Chefão', 'Drama', 'Francis Ford Coppola', 1972, 25.90);
INSERT INTO filmes (titulo, genero, diretor, ano_lancamento, preco) VALUES ('Pulp Fiction', 'Crime', 'Quentin Tarantino', 1994, 29.90);
INSERT INTO filmes (titulo, genero, diretor, ano_lancamento, preco) VALUES ('O Senhor dos Anéis: A Sociedade do Anel', 'Fantasia', 'Peter Jackson', 2001, 35.90);
INSERT INTO filmes (titulo, genero, diretor, ano_lancamento, preco) VALUES ('Matrix', 'Ficção Científica', 'Lana Wachowski, Lilly Wachowski', 1999, 27.50);
INSERT INTO filmes (titulo, genero, diretor, ano_lancamento, preco) VALUES ('Forrest Gump', 'Drama', 'Robert Zemeckis', 1994, 22.90);
INSERT INTO filmes (titulo, genero, diretor, ano_lancamento, preco) VALUES ('Gladiador', 'Ação', 'Ridley Scott', 2000, 30.00);
INSERT INTO filmes (titulo, genero, diretor, ano_lancamento, preco) VALUES ('Titanic', 'Romance', 'James Cameron', 1997, 28.90);
INSERT INTO filmes (titulo, genero, diretor, ano_lancamento, preco) VALUES ('Star Wars: O Império Contra-Ataca', 'Ficção Científica', 'Irvin Kershner', 1980, 33.90);
INSERT INTO filmes (titulo, genero, diretor, ano_lancamento, preco) VALUES ('O Exterminador do Futuro 2: O Julgamento Final', 'Ação', 'James Cameron', 1991, 26.50);
INSERT INTO filmes (titulo, genero, diretor, ano_lancamento, preco) VALUES ('Coringa', 'Drama', 'Todd Phillips', 2019, 32.00);

SELECT * FROM filmes

1. SELECT * FROM estoque_filmes where id = 2

2. SELECT 
    f.titulo, 
    e.quantidade, 
    e.status
FROM 
    filmes f
JOIN 
    estoque_filmes e ON f.id = e.filme_id
WHERE 
    f.id = 3;
    
3. UPDATE estoque_filmes
SET quantidade = quantidade - 1, status = 'Alugado'
WHERE filme_id = 1 AND quantidade > 0;

4. UPDATE estoque_filmes
SET quantidade = quantidade + 1, status = 'Disponível'
WHERE filme_id = 2;

5. SELECT 
    f.titulo, 
    f.genero, 
    f.diretor, 
    f.ano_lancamento, 
    e.quantidade
FROM 
    filmes f
JOIN 
    estoque_filmes e ON f.id = e.filme_id
WHERE 
    e.status = 'Disponível' AND e.quantidade > 0;
    
6. SELECT 
    f.titulo, 
    f.genero, 
    f.diretor, 
    f.ano_lancamento, 
    e.quantidade
FROM 
    filmes f
JOIN 
    estoque_filmes e ON f.id = e.filme_id
WHERE 
    e.status = 'Em Manutenção';
    
7. UPDATE estoque_filmes
SET status = 'Em Manutenção'
WHERE filme_id = 3;
