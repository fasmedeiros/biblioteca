# biblioteca
Sistema de Biblioteca

````mermaid
classDiagram
    class Usuario {
        int id
        String nome
        String email
        String senha
        Date dataCadastro
        +cadastrar()
        +fazerLogin()
        +reservarLivro()
        +renovarEmprestimo()
        +visualizarHistorico()
    }

    class Bibliotecario {
        int id
        String nome
        String email
        String senha
        Date dataContratacao
        +adicionarLivro()
        +atualizarLivro()
        +removerLivro()
        +gerenciarUsuario()
    }

    class Livro {
        String isbn
        String titulo
        String autor
        String genero
        int numPaginas
        Boolean disponibilidade
        +consultarDetalhes()
    }

    class Emprestimo {
        int id
        int usuarioId
        String livroIsbn
        Date dataEmprestimo
        Date dataDevolucao
        String status
        +registrarEmprestimo()
        +renovarEmprestimo()
        +calcularMulta()
    }

    class Biblioteca {
        String nome
        String endereco
        List<Livro> livros
        List<Usuario> usuarios
        List<Emprestimo> emprestimos
        +adicionarLivro()
        +removerLivro()
        +buscarLivro()
        +gerenciarEmprestimos()
        +gerenciarUsuarios()
    }

    Usuario "1" --o "0..*" Emprestimo : realiza
    Livro "1" --o "0..*" Emprestimo : está envolvido em
    Biblioteca "1" --o "0..*" Livro : possui
    Biblioteca "1" --o "0..*" Usuario : possui
    Biblioteca "1" --o "0..*" Emprestimo : gerencia
    Bibliotecario "1" --o "0..*" Livro : gerencia

