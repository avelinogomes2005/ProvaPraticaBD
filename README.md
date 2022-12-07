# Respostas Prova Prática de Banco de Dados SQL (consultas/resultado)
< h3 align = "center" > Aluno: Raimundo Avelino Gomes Lima | 2°  Informática | PROFESSOR: Adeilson Sales Aragão </h3>


## Dados das Tabelas:
create table TB_aluno(
   cod_aluno int primary key,
	nome_aluno varchar(50) NOT NULL,
	ano_nascimento date,
	e_mail varchar(60),
	sexo varchar NOT NULL
);

create table TB_Curso (
   cod_curso int primary key,
	nome_curso varchar (60) NOT NULL
);

create table TB_Matricula (
   cod_curso int references TB_curso (cod_curso),
	cod_aluno int references TB_aluno (cod_aluno)
);



## Questão 1:
Faça um comando SQL para matricular o aluno “Pedro César” no curso de
Informática. Os dados devem ser inseridos na tabela TB_MATRÍCULA.

```sql
select * from tb_aluno

insert into tb_aluno(codigo_aluno, nome_aluno, ano_nasc, email, sexo)
values ('4', 'Pedro César', '1995-06-04', 'pedro@provaSQL.com.br', 'M')

select * from tb_matricula

insert into tb_matricula(codigo_curso, codigo_aluno)
values ('4', '4')
```
## Resultado:




## Questão 2:
Escreva um comando SQL que retorne os nomes dos alunos e do(s) cursos em
que estão matriculados. Os dados deverão estar ordenados pelo nome do curso.

```sql
select tb_aluno.nome_aluno, tb_curso.nome_curso
from tb_aluno
inner join tb_matricula
on tb_aluno.codigo_aluno = tb_matricula.codigo_aluno
inner join tb_curso
on tb_curso.codigo_curso = tb_matricula.codigo_curso
```
## Resultado:





## Questão 3:
Crie um comando SQL que retorne o e-mail de todos os alunos maiores de idade.
```sql
select email
from tb_aluno where 2022 - ano_nasc >= 18
```
## Resultado:




## Questão 4:
Desenvolva um comando SQL que mostre o total de alunos.
```sql
select count(codigo_aluno)
from tb_aluno
```
## Resultado:





## Questão 5:
Escreva um comando SQL para listar o total de alunos matriculador em cada curso.
```sql
select tb_curso.nome_curso,
codigo_curso + codigo_aluno as numero_alunos
from tb_curso
inner join tb_aluno
on tb_aluno.codigo_aluno = tb_curso.codigo_curso
```
## Resultado:




## Questão 6:
Desenvolva um comando SQL que retorne o nome de todos os alunos maiores que
18 anos.
```sql
select nome_aluno
from tb_aluno where 2022 - ano_nasc >= 18
```
## Resultado:




## Questão 7:
```sql
select nome_aluno, sexo
from tb_aluno where sexo = 'F'
```
## Resultado:





## Questão 8:
```sql
select tb_aluno.nome_aluno as mulheres_em_medicina
from tb_aluno
inner join tb_matricula
on tb_matricula.codigo_aluno = tb_aluno.codigo_aluno
and tb_matricula.codigo_curso = 1
and tb_aluno.sexo = 'F'
```
## Resultado:





## Questão 9:
```sql
select nome_curso
from tb_curo order by nome_curso asc
```
## Resultado:






## Questão 10:
```sql
select tb_aluno.nome_aluno as homens_em_Jornalismo
from tb_aluno
inner join tb_matricula
on tb_matricula.codigo_aluno = tb_aluno.codigo_aluno
and tb_matricula.codigo_curso = 5
and tb_aluno.sexo = 'M'
```
## Resultado:

