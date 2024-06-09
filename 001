Descrição: Testando um Componente Angular com Chamada de API AWS

Cenário: Este teste verifica se um componente Angular está buscando dados corretamente de uma API AWS.

Código:

JavaScript
describe('MeuComponente', () => {
  it('deve buscar dados da API AWS', () => {
    // Carregar o componente
    cy.visit('/meu-componente');

    // Verificar se os dados foram buscados da API
    cy.get('.dados-api').should('contain', 'Dados da API AWS');

    // Verificar se a requisição para a API foi feita
    cy.request({
      url: 'https://api.aws.example.com/dados',
      method: 'GET'
    }).should((response) => {
      expect(response.status).to.equal(200);
      expect(response.body).to.deep.equal({ dados: ['data1', 'data2'] });
    });
  });
});
