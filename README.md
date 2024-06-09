Descrição: Testando uma Interação com o Amazon AWS DynamoDB (Teste de Integração)

Cenário: Este teste verifica se um aplicativo Angular pode gravar e recuperar dados do Amazon DynamoDB.

Teste Código: JavaScript

describe('Interação com DynamoDB', () => {
  it('deve gravar e recuperar dados do DynamoDB', () => {
    // Carregar a página de dados
    cy.visit('/dados');

    // Preencher o formulário com dados
    cy.get('#nome-input').type('Nome');
    cy.get('#email-input').type('email@exemplo.com');

    // Salvar os dados no DynamoDB
    cy.get('#botao-salvar').click();

    // Verificar se os dados foram gravados no DynamoDB
    cy.request({
      url: 'https://dynamodb.amazonaws.com/my-table/item/1',
      method: 'GET'
    }).should((response) => {
      expect(response.status).to.equal(200);
      expect(response.body).to.deep.equal({ nome: 'Nome', email: 'email@exemplo.com' });
    });

    // Buscar os dados do DynamoDB
    cy.get('#botao-buscar
