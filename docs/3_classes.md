@startuml

class Aluno {
 - idAluno: 
 - nome: 
 - cpf: 
 - email: 
 - telefone: 
 - endereco: 
 - rfid: 
 - status: 
  
 - contratarPlano(): 
 - visualizarHorarios(): 
 - agendarAula(): 
 - cancelarAgendamento(): 
 - atualizarStatus(): 
 - registrarAcesso(): 
 - receberNotificacao(): 
}

class Plano {
 - idPlano: 
 - nome: 
 - tipo: 
 - valor: 
 - ativo: 
  
 - criar(): 
 - editar(): 
 - ativar(): 
 - desativar(): 
}

class Pagamento {
 - idPagamento: 
 - data: 
 - valor: 
 - formaPagamento: 
 - status: 
  
 - registrar():
 - confirmar():
 - cancelar():
}

class Acesso {
 - idAcesso: 
 - dataHora: 
 - autorizado: 
  
 - validarEntrada(): 
}

class Aula {
 - idAula: 
 - nome: 
 - horario: 
 - capacidadeMaxima: 
  
 - verificarVagas(): 
}

class Agendamento {
 - idAgendamento: 
 - dataReserva: 
 - status: 
  
 - confirmar(): 
 - cancelar(): 
}

class Presenca {
 - idPresenca: 
 - data: 
 - presente: 
  
 - registrar(): 
}

class AvaliacaoFisica {
 - idAvaliacao: 
 - data: 
 - peso: 
 - imc: 
 - percentualGordura: 
 - observacoes: 
 - anexo: 
  
 - calcularIMC(): 
 - anexarArquivo(): 
}

class Notificacao {
 - idNotificacao: 
 - tipo: 
 - dataEnvio: 
 - status: 
 - mensagem: 
  
 - enviarNotificacao(): 
 - marcarLida():
}

abstract class Funcionario {
 - idFuncionario: 
 - nome: 
}

class Instrutor {
 - especialidade: 
  
 - registrarPresenca(): 
 - registrarAvaliacaoFisica(): 
}

class Recepcionista {
 - cadastrarAluno(): 
 - registrarPagamento(): 
}

class Gerente {
 - emitirRelatorios(): 
}

- Funcionario <|-- Instrutor
- Funcionario <|-- Recepcionista
- Funcionario <|-- Gerente

- Aluno "1" -- "1" Plano : contrata
- Aluno "1" -- "0..*" Pagamento : realiza
- Aluno "1" -- "0..*" Acesso : gera
- Aluno "1" -- "0..*" Agendamento : realiza
- Aluno "1" -- "0..*" Presenca : possui
- Aluno "1" -- "0..*" AvaliacaoFisica : possui
- Aluno "1" -- "0..*" Aula : participa
- Aluno "1" -- "0..*" Notificacao : recebe

- Aula "1" -- "0..*" Agendamento : possui
- Aula "1" -- "0..*" Presenca : registra

- Instrutor "1" -- "0..*" Aula : ministra
- Instrutor "1" -- "0..*" AvaliacaoFisica : realiza
- Instrutor "1" -- "0..*" Presenca : registra

@enduml
