# E2E Testing - Best practices

## 1. Übersicht

### 1.1 E2E Testing Frameworks

* [Cypress](https://www.cypress.io)
* [Selenium WebDriver](https://www.seleniumhq.org/projects/webdriver)

## 2. Best Practices

Nachfolgende genannte bewährte Verfahren beziehen sich auf alle Testverfahren und sind Framework- und Tool-unabhängig. Genannte Codebeispiele beziehen sich auf auf das Cypress Framework.

### 2.1 Login

* Logge dich nicht über die GUI ein (langsam und durchaus fehleranfällig)
* Logge dich programmgesteuert in deine Anwendung ein
  * übernimm die Kontrolle deiner Anwendung: Setze den Login-Status direkt beim Testen
* Einzige Ausnahme: Du testest den Login-Prozess direkt

### Selektoren

* Verwende keine Design-gebundenen Selektoren (CSS, classes, Tags, etc.)
** diese können sich ändern und brechen damit den Test
* Verwende Design-ungebundene Selektoren (data Attribute, Text, etc.)
** Diese werden nur für das Testing verwendet
** Text-Tests sind wichtig, wenn der Test abhängig vom Text ist (Speichern vs. Abbrechen)

Beispiel:

`<button id="main-button" class="btn btn-save" data-cy="save">Save</button>`

* Niemals (*kein Kontext*): `cy.get('button').click()`
* Auch nicht (*kann sich bei Designänderungen ändern*): `cy.get('.btn.btn-save').click()`
* Besser (*nicht eindeutig ersichtlich, dass diese ID zum testen verwendet wird*): `cy.get('#main-button').click()`
* OK (*nur wenn Textänderungen den Test brechen sollen*): `cy.contains('Save').click()`
  * z.B. Text ändert sich von "Save" zu "Cancel"
* Optimal (*eindeutig ersichtlich, dass dieses Attribut zum Testen verwendet wird*): `cy.get('[data-cy=save]').click()`

## A. Weitere Anleitungen

* Todo..

## B. Quellen

* [Best practices - Cypress](https://docs.cypress.io/guides/references/best-practices.html)

## C. Tools

* Todo..

## D. Fußnoten

* <sup>1</sup> = ..

## E. Autoren

* Björn Hempel <bjoern@hempel.li> - _Erste Arbeiten_ - [https://github.com/bjoern-hempel](https://github.com/bjoern-hempel)

## F. Lizenz

Dieses Tutorial steht unter der MIT-Lizenz - siehe die Datei [LICENSE.md](/LICENSE.md) für weitere Informationen.
