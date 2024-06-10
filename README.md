# Loca-o-de-Autom-veis

CREATE TABLE Veiculo (
Veiculo VARCHAR(50) PRIMARY KEY,
Cor VARCHAR(50),
Placa VARCHAR(10)
);

CREATE TABLE Cliente (
Cliente VARCHAR(50) PRIMARY KEY,
CPF VARCHAR(14),
Nascimento DATE
);

CREATE TABLE Locacao (
CodLocacao INT PRIMARY KEY,
Veiculo VARCHAR(50) FOREIGN KEY REFERENCES Veiculo(Veiculo),
Diaria DECIMAL(10,2),
Cliente VARCHAR(50) FOREIGN KEY REFERENCES Cliente(Cliente),
Dias INT,
Total DECIMAL(10,2)
);

CREATE VIEW VW_Locacoes AS
SELECT
l.CodLocacao,
v.Veiculo,
v.Cor,
v.Placa,
l.Diaria,
c.Cliente,
c.CPF,
c.Nascimento,
l.Dias,
l.Total
FROM Locacao l
JOIN Veiculo v ON l.Veiculo = v.Veiculo
JOIN Cliente c ON l.Cliente = c.Cliente;

INSERT INTO Locacao (
  `Cód. Locação`,
  Veículo,
  Cor,
  Placa,
  Diária,
  Cliente,
  CPF,
  Nascimento,
  Dias,
  Total
) VALUES (
  101,
  'Fusca',
  'Preto',
  'WER-3456',
  30.00,
  'Ariano Suassuna',
  '123.456.789-01',
  '2022-05-21',
  3,
  90.00),
(
   102,
  'Variante',
  'Rosa',
  'FDS-8384',
  60.00,
  'Grace Hopper',
  '543.765.987-23',
  '2002-04-29',
  7,
  420.00),
(
   103,
  'Comodoro',
  'Rosa',
  'CVB-9933',
  20.00,
  'Richard Feynman',
  '987.654.231-90',
  '2001-12-10',
  1,
  20.00),
(
   104,
  'Delorian',
  'Azul',
  'FGH-2256',
  80.00,
  'Edgar Poe',
  '432.765.678-67',
  '1998-12-14',
  3,
  240.00),
(
   105,
  'Brasília',
  'Amarela',
  'DDI-3948',
  45.00,
  'Gordon Freeman',
  '927.384.284-44',
  '1984-11-26',
  7,
  315.00),
CREATE VIEW vw_locacoes AS
SELECT 
  l.id_locacao,
  l.data_inicio,
  l.data_fim,
  l.valor,
  v.placa,
  v.cor,
  m.nome_modelo,
  ma.nome_marca,
  c.nome,
  c.cpf,
  c.telefone,
  ci.nome_cidade,
  e.nome_estado
FROM Locacao l
JOIN Veículo v ON l.id_veiculo = v.id_veiculo
JOIN Modelo m ON v.id_modelo = m.id_modelo
JOIN Marca ma ON m.id_marca = ma.id_marca
JOIN Cliente c ON l.id_cliente = c.id_cliente
JOIN Cidade ci ON c.id_cidade = ci.id_cidade
JOIN Estado e ON ci.id_estado = e.id_estado;
