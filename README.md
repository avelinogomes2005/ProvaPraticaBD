# Respostas Prova Prática de Banco de Dados SQL (consultas/resultado)
🔰 Aluno: Raimundo Avelino Gomes Lima | 2°  Informática | PROFESSOR: Adeilson Sales Aragão


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
![IMG1](https://user-images.githubusercontent.com/102837037/206235258-97676e08-e50c-4df7-8193-e1d26eee7466.PNG)
![IMG2](https://user-images.githubusercontent.com/102837037/206235275-f216cd4d-4d1b-4cd2-92fb-5c3e14872df9.PNG)



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
![IMG1](https://user-images.githubusercontent.com/102837037/206235329-e8d9ba0d-3169-40d9-991b-f80d2f48221f.PNG)



## Questão 3:
Crie um comando SQL que retorne o e-mail de todos os alunos maiores de idade.
```sql
select email
from tb_aluno where 2022 - ano_nasc >= 18
```
## Resultado:
![IMG1](https://user-images.githubusercontent.com/102837037/206235399-3884b465-f303-4021-b363-b02d85b3c44b.PNG)



## Questão 4:
Desenvolva um comando SQL que mostre o total de alunos.
```sql
select count(codigo_aluno)
from tb_aluno
```
## Resultado:
![IMG1](https://user-images.githubusercontent.com/102837037/206235491-a575d51c-2c60-4b95-98ed-ed2042ffa66b.PNG)



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
![IMG1](https://user-images.githubusercontent.com/102837037/206235551-e11e4c5b-9c8a-4bf4-9c62-4d96a6411e7f.PNG)



## Questão 6:
Desenvolva um comando SQL que retorne o nome de todos os alunos maiores que
18 anos.
```sql
select nome_aluno
from tb_aluno where 2022 - ano_nasc >= 18
```
## Resultado:
![IMG1](https://user-images.githubusercontent.com/102837037/206235606-afe5c319-a082-46b6-ae49-9907d140cbc7.PNG)



## Questão 7:
```sql
select nome_aluno, sexo
from tb_aluno where sexo = 'F'
```
## Resultado:
![IMG1](https://user-images.githubusercontent.com/102837037/206235634-2d1d2a50-26ce-4687-a27d-94a577db9ad0.PNG)



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
![IMG1](https://user-images.githubusercontent.com/102837037/206235673-7e9efc51-8f05-46f2-b4c0-bbfbb7c6ee7f.PNG)



## Questão 9:
```sql
select nome_curso
from tb_curo order by nome_curso asc
```
## Resultado:
![IMG1](https://user-images.githubusercontent.com/102837037/206235734-5b504276-4b32-44d6-bdbe-3f95b0adf3ac.PNG)



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

