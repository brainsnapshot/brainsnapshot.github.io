---
layout: page
title: "Domain Events"
---

# Domain Events

Pojęcie Domian Event mocno związane jest z tematem DDD, ale podobnie jak reszta terminów z DDD może być implementowana niezależnie.
Eventy mają symbolizować wydarzenia biznesowe które wydarzyły się w przeszłości np. PaymentPaid.  

### Cechy podstawowe:
1. Powinien być serializowalny, głównie po to żeby go przesyłać po sieci.
+ Nazwa powinna być napisana w czasie przeszłym dokonanym.
Powinny oznajmiać  fakt, a nie życzenie.
+ Jedno zdarzenie ma jedno źródło.
 jeżeli tak nie jest to znaczy że odkryliśmy jeszcze wszystkich pojęć domenowych.
+ Raz rozesłany event nie może zostać zatrzymany, powinien być rozpropagowany po całym systemie.
Dlaczego: Głównie ze względu no idące z tym komplikacje, przykładowo na event podpiętych jest 10 listenerów, które odpalają się w różnej kolejności, piąty z kolei wykrzacza system, reszta się nie wykonuje.
+ Listenery podpięte pod event nie powinny nic o sobie wiedzieć, nie liczyć na kolejność w jakiej są podpięte, czy kiedy się wywołają.
+ Wykorzystanie eventów jest jedną z technik utraty kontroli

### Cechy rekomendowane
1. event powinien być mały
* dokładność czasu zdarzenia, nie w milisekundach a mikrosekundach

### Zalecenia
* Powinieneś posiadać system który loguje eventy, a ty możesz po nich wyszukiwać.
* Nie modeluj zdarzenia dla konkretnego handlera

### Legacy
Zdarzenia pomagają w wydzielaniu logiki z systemów Legacy, aby zmniejszyć ilość kodu, i ilość odpowiedzialność w nietestowanych systemach. W łatwy sposób można pozbyć się kodu odpowiedzialnego np za powiadomienia.

### Implementacje
* Rise events
* Event-Dispatcher w obiektach domenowych

### Inne:
Synchroniczność/asynchroniczność

### Pytania:
* Czy event powinien być mały?
* Gdzie tworzyć zdarzenia domenowe?
 * http://rosstuck.com/domain-events-on-creation
* Czy event powinien składać się z prymitywów czy z obiektów domenowych?


### Powiązane pojęcia
* Wzorzec SAGA
* Event Sourcing
* Event Storming
* Event Driven Architecture


### Do analizy:
http://danielwhittaker.me/2016/04/20/how-to-validate-commands-in-a-cqrs-application/

### Źródła:
1) Wykład:
Mateusz Stasch Domain Events - czyli jak radzić sobie z rzeczywistością
Wideo: https://www.youtube.com/watch?v=hHGCBBbCuEk
Prezentacja: https://www.slideshare.net/proidea_conferences/mateusz-stasch-domain-events-czyli-jak-radzi-sobie-z-rzeczywistoci
