const minhaImagem = document.getElementById('minhaImagem');
minhaImagem.src = 'logoapae.jpg'; // ou 'logoapae.png', dependendo do formatolet alunos = [];let alunos = [];

function carregarDados() {
    const dados = localStorage.getItem('alunos');
    if (dados) {
        alunos = JSON.parse(dados);
        atualizarListaAlunos();
        atualizarSelectAlunos();
    }
}

function salvarDados() {
    localStorage.setItem('alunos', JSON.stringify(alunos));
}

function cadastrarAluno() {
    const nome = document.getElementById('nome').value;
    const matricula = document.getElementById('matricula').value;
    const contato = document.getElementById('contato').value;
    const documento = document.getElementById('documento').value;

    alunos.push({ nome, matricula, contato, documento, presenca: {} });
    salvarDados();
    atualizarListaAlunos();
    atualizarSelectAlunos();
    document.getElementById('formCadastro').reset();
}

function atualizarListaAlunos() {
    const lista = document.getElementById('alunosCadastrados');
    lista.innerHTML = '';
    alunos.forEach((aluno, index) => {
        const item = document.createElement('li');
        item.textContent = aluno.nome;

        const botaoEditar = document.createElement('button');
        botaoEditar.textContent = 'Editar';
        botaoEditar.onclick = () => editarAluno(index);
        item.appendChild(botaoEditar);

        const botaoExcluir = document.createElement('button');
        botaoExcluir.textContent = 'Excluir';
        botaoExcluir.onclick = () => excluirAluno(index);
        item.appendChild(botaoExcluir);

        lista.appendChild(item);
    });
}

function atualizarSelectAlunos() {
    const select = document.getElementById('alunoPresenca');
    select.innerHTML = '';
    alunos.forEach((aluno, index) => {
        const option = document.createElement('option');
        option.value = index;
        option.textContent = aluno.nome;
        select.appendChild(option);
    });
}

function marcarPresenca() {
    const alunoIndex = document.getElementById('alunoPresenca').value;
    const data = new Date().toLocaleDateString();
    alunos[alunoIndex].presenca[data] = 'presente';
    salvarDados();
}

function marcarAusencia() {
    const alunoIndex = document.getElementById('alunoPresenca').value;
    const data = new Date().toLocaleDateString();
    alunos[alunoIndex].presenca[data] = 'ausente';
    salvarDados();
}

function gerarRelatorio() {
    const nome = document.getElementById('relatorioNome').value;
    const data = document.getElementById('relatorioData').value;
    const resultado = document.getElementById('resultadoRelatorio');
    resultado.innerHTML = '';

    const aluno = alunos.find(a => a.nome === nome);
    if (aluno && aluno.presenca[data]) {
        resultado.textContent = `Aluno: ${nome}, Data: ${data}, Presen�a: ${aluno.presenca[data]}`;
    } else {
        resultado.textContent = 'Relatório não encontrado.';
    }
}

function editarAluno(index) {
    const aluno = alunos[index];
    document.getElementById('nome').value = aluno.nome;
    document.getElementById('matricula').value = aluno.matricula;
    document.getElementById('contato').value = aluno.contato;
    document.getElementById('documento').value = aluno.documento;

    alunos.splice(index, 1);
    salvarDados();
    atualizarListaAlunos();
    atualizarSelectAlunos();
}

function excluirAluno(index) {
    alunos.splice(index, 1);
    salvarDados();
    atualizarListaAlunos();
    atualizarSelectAlunos();
}

carregarDados();
