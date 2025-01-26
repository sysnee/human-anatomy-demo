# Documentação do Componente Human Body Map v1.0

## Índice
1. [Introdução](#introdução)
2. [Instalação](#instalação)
3. [Uso Básico](#uso-básico)
4. [Propriedades](#propriedades)
5. [Eventos](#eventos)
6. [Exemplos](#exemplos)
7. [Compatibilidade](#compatibilidade)
8. [Solução de Problemas](#solução-de-problemas)

## Introdução

O Human Body Map é um componente web interativo que permite a visualização e interação com diferentes sistemas do corpo humano. O componente oferece:

- Visualização interativa do corpo humano
- Seleção de diferentes sistemas anatômicos
- Identificação e seleção de órgãos específicos
- Exibição de achados médicos quando um CPF é fornecido
- Feedback visual em tempo real para interações do usuário

## Instalação

### Uso via CDN
html
<script type="module" src="https://d2343lbggy2b29.cloudfront.net/human-body-map-illustration-[version].js"></script>


> **Nota Importante**: Quando implementado em webview, certifique-se de que o JavaScript esteja habilitado para o funcionamento correto do componente.

## Uso Básico

Adicione o componente ao seu HTML:

html
<human-body-map
    cpf="12345678900"
    access-key="sua-chave-de-acesso">
</human-body-map>


> **Nota**: O CPF é opcional. Sem ele, o componente funcionará normalmente, mas não exibirá nenhum achado médico associado.

## Propriedades

| Propriedade | Tipo | Descrição | Obrigatório |
|-------------|------|-----------|-------------|
| cpf | String | CPF do paciente para exibição de achados | Não |
| access-key | String | Chave de autenticação para acesso à API | Sim |
| selected-system | String | Sistema do corpo atualmente selecionado | Não |
| selected-organ | String | Órgão atualmente selecionado | Não |

## Interatividade

O componente oferece diversas formas de interação:

1. **Hover sobre órgãos**:
   - Ao passar o mouse sobre um órgão, ele é destacado e seu nome é exibido
   - Feedback visual imediato para facilitar a identificação

2. **Seleção de Sistemas**:
   - Clique em botões de sistema para alternar entre diferentes visualizações
   - A imagem de fundo muda dinamicamente para mostrar o sistema selecionado

3. **Seleção de Órgãos**:
   - Clique em órgãos específicos para selecioná-los
   - O órgão selecionado fica destacado em azul
   - Exibe informações detalhadas quando há achados associados ao CPF

## Eventos

O componente emite os seguintes eventos personalizados:

### organ-click
Disparado quando um órgão é clicado.

javascript
bodyMap.addEventListener('organ-click', (e) => {
    console.log('Selecionado:', e.detail);
    // e.detail = { system: "Sistema Nervoso", organ: "Cérebro" }
});


### reset-filter
Disparado quando os filtros são resetados.

javascript
bodyMap.addEventListener('reset-filter', () => {
    console.log('Filtros foram resetados');
});


## Exemplos

### Demonstração Online
Você pode ver um exemplo funcional do componente no JSFiddle:
[Human Body Map Demo](https://jsfiddle.net/sysnee/zv9tbhsm/3/)

### Implementação Básica
html
<!DOCTYPE html>
<html>
<head>
    <script type="module" src="https://d2343lbggy2b29.cloudfront.net/human-body-map-illustration-[version].js"></script>
</head>
<body>
    <human-body-map
        id="bodyMap"
        cpf="12345678900"
        access-key="chave-demo">
    </human-body-map>
</body>
</html>


### Implementação com Botões de Sistema
html
<div class="system-buttons">
    <button class="system-button" data-system="default">Visão Geral</button>
    <button class="system-button" data-system="Sistema Nervoso">Sistema Nervoso</button>
    <!-- Adicione outros botões de sistema conforme necessário -->
</div>

<human-body-map id="bodyMap"></human-body-map>

<script>
    const bodyMap = document.getElementById('bodyMap');
    const buttons = document.querySelectorAll('.system-button');

    buttons.forEach(button => {
        button.addEventListener('click', () => {
            const system = button.dataset.system;
            if (system === 'default') {
                bodyMap.resetOrganFilter();
            } else {
                bodyMap.selectedSystem = system;
            }
        });
    });
</script>


## Estilização

O componente pode ser estilizado usando CSS:

css
human-body-map {
    width: 100%;
    height: 500px;
    display: block;
}


## Solução de Problemas

### Problemas Comuns

1. **Componente Não Carrega**
   - Verifique se o script está carregado corretamente
   - Verifique se o JavaScript está habilitado
   - Verifique se a chave de acesso é válida

2. **Imagens Não Aparecem**
   - Verifique a conexão com a internet
   - Verifique o acesso ao CDN
   - Verifique a configuração de CORS

3. **Eventos Não Funcionam**
   - Verifique a implementação dos event listeners
   - Verifique o console do navegador para erros
   - Certifique-se de que o componente está montado corretamente

### Mensagens de Erro

| Erro | Causa | Solução |
|------|-------|---------|
| "Invalid access key" | Chave de acesso inválida ou expirada | Verificar validade da chave |
| "Sistema inválido" | Seleção de sistema inválida | Verificar nome do sistema |
| "Error fetching data" | Erro de rede ou API | Verificar conexão e status da API |

## Suporte

Sinta-se a vontade para reportar problemas e tirar dúvidas!
---