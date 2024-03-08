# Projeto de Automação com Cypress

## Testes Cypress

Este projeto utiliza Cypress para automação de testes. Abaixo estão os principais testes realizados nas funcionalidades de login, cadastro e produtos.

### Login

- **Login com sucesso:**
  - Navega até a página de login.
  - Preenche os campos de usuário e senha.
  - Verifica se o login é bem-sucedido.

  ```javascript
  // Exemplo de código Cypress para o teste de login com sucesso
  it('Deve fazer login com sucesso', () => {
    cy.visit('http://lojaebac.ebaconline.art.br/minha-conta/');
    cy.get('#username').type('ivapmn@test.art.br');
    cy.get('#password').type('123456');
    cy.get('.woocommerce-form > .button').click();
    cy.get('.woocommerce-MyAccount-content > :nth-child(2)').should('contain', 'Olá, ivapmn (não é ivapmn? Sair)');
  });
  Cadastro
//Cadastro com sucesso:

//Preenche campos de e-mail e senha com valores aleatórios usando a biblioteca Faker.
//Verifica se o cadastro foi concluído com sucesso.

// Exemplo de código Cypress para o teste de cadastro com sucesso
it('Deve completar o cadastro com sucesso', () => {
  cy.get('#reg_email').type(faker.internet.email());
  cy.get('#reg_password').type("Ter4563");
  cy.get(':nth-child(4) > .button').click();
  cy.get('.woocommerce-MyAccount-content > :nth-child(2)').should('exist');
  cy.get('.woocommerce-MyAccount-navigation-link--edit-account > a').click();
  cy.get('#account_first_name').type(faker.person.firstName());
  cy.get('#account_last_name').type(faker.person.lastName());
  cy.get('.woocommerce-Button').click();
  cy.get('.woocommerce-message').should('contain','Detalhes da conta modificados com sucesso.');
});

//Produtos
//Seleção de Produto:

//Navega até a página de produtos.
//Seleciona o primeiro produto da lista.
//Verifica se a aba de descrição está presente.

// Exemplo de código Cypress para o teste de seleção de produto
it('Deve selecionar um produto da lista', () => {
  cy.visit('http://lojaebac.ebaconline.art.br/produtos/');
  cy.get('.product-block ').first().click();
  cy.get('#tab-title-description > a').should('contain','Descrição');
});
