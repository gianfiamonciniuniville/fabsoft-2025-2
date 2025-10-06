# Fábrica de Software 2025/2

#### Gian Carlo Fiamoncini e Carlos Alberto

## Propostas de projeto

#### Sistema de Blogs, com comentários e moderadores

## Links Of Repos

#### Back-end: https://github.com/gianfiamonciniuniville/UniBlogBackEnd

#### Front-end:

## Tecnologias

- Backend em C# .NET Arquitetura Onion Entity Framework,
- Banco de Dados SQL SERVER via docker,
- Frontend em REACT TS (Framework a decidir)

## Histórias do Usuário

## Diagrama de Entidade e Relacionamento
```mermaid
classDiagram
direction LR
    class Entity-Classe-Abstrata {
	    +int Id
	    +DateTime Created_at
	    +DateTime Updated_at
    }

    class Blog {
	    +string Title
	    +string Description
	    +int UserId
	    +GetAllWithDetailsAsync()
	    +GetByIdWithDetailsAsync(int id)
	    +CreateAsync(Blog blog)
	    +UpdateAsync(Blog blog)
	    +DeleteAsync(int id)
    }

    class User {
	    +string UserName
	    +string Email
	    +string PasswordHash
	    +string? ProfileImageUrl
	    +string? Bio
	    +string Role
	    +CreateAsync(User user)
	    +GetByEmailAsync(string email)
	    +GetByIdAsync(int id)
	    +GetByUserNameAsync(string userName)
	    +UpdateAsync(User user)
    }

    class Post {
	    +int BlogId
	    +int AuthorId
	    +string Title
	    +string Content
	    +string Slug
	    +bool Published
	    +DateTime? PublishedAt
	    +int ViewCount
	    +GetAllWithDetailsAsync()
	    +GetByIdAsync(int id)
	    +GetBySlugWithDetailsAsync(string slug)
	    +GetByAuthorWithDetailsAsync(int authorId)
	    +UpdateAsync(Post post)
	    +CreateAsync(Post post)
    }

    class Comment {
	    +int PostId
	    +int UserId
	    +string Content
	    +CreateAsync(Comment comment)
	    +DeleteAsync(int id)
    }

    class Like {
	    +int PostId
	    +int UserId
	    +CreateAsync(Like like)
	    +DeleteAsync(int id)
	    +GetByPostAndUserAsync(int postId, int userId)
    }

    User "1" o-- "N" Blog : (UserId)
    Blog "1" o-- "N" Post : (BlogId)
    User "1" o-- "N" Post : (AuthorId)
    Post "1" o-- "N" Comment : (PostId)
    User "1" o-- "N" Comment : (UserId)
    Post "1" o-- "N" Like : (PostId)
    User "1" o-- "N" Like : (UserId)


```
