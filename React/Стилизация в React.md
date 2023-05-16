# Стилизация в React

## Инлайн стили
__`Inline-style`__ – помещаются в атрибут `style` в виде объекта, где названия полей (css-свойств) пишутся в `camelCase`.

```javascript
<element style={{ justifyText: ‘left’, fontSize: 40, lineHeight: 40 + 'em' }} />
// пиксели указвать не надо (другие единицы оборачиваются в строки)
```

<br>

## Динамические стили
Вариант задания стилей динамически на этапе рендера компонента, в ходе которого на основе `props`, `state` или прочего - задаются определенные `инлайн-стили` (атрибут `style`) или классы (атрибут`className`).

<br>

## SASS-препроцессор
`LESS`-препроцессор и другие на данный момент в `React` не поддерживаются. Чтобы подключить SASS-препроцессор к проекту нужно установить его npm-пакет:

```
// именно прод-установка - чтобы работал и на хостинге
npm i sass --save
```

Подключить файл-стилей к модулю можно простым импортированием файла:
```javascript
import "./style.css"
import "./style.scss"
```

Если внутри файла-стиля мы хотим использовать `sass-переменные` из отдельного файла - мы должны импортировать его в каждый такой файл:
```css
@import "../variables.scss"

div { color: $main-color }
```

<br>

## Библиотеки стилей

### 💅🏾[Styled Components](https://styled-components.com/)

Популярная библиотека, которая реализует подход `CSS-in-JS` - позволяет размещать стили комопнента или элемента внутри его модуля:  
```
// устанавливаем в проект как прод-зависимость
npm i styled-components 
```
```javascript
// импортируем сущность в модуль
import styled from 'styled-components'
```

Используем внутри модуля компонента:  
```javascript
const Button = styled.a`
  обычный CSS код...
  
  // или можно использовать условие внутри стиля
  ${props => props.$primary && css`
    background: white;
    color: black;
  `}
`
```

Принцип работы:  
* `styled.a` - означает что элемент попадет в DOM-дерево в виде `<a>-тега`;
* ` CSS-код... ` - код стилей помещается сразу после внутри бэк-тиков;
* Чтобы назначить эти стили готовому DOM-элементу - библиотека присвоит ему класс с сгенерированным именем;

<br>

### [React Bootstrap](https://react-bootstrap.github.io/)

Упрощает взаимодействие с `bootstrap` внутри `react`-приложения:  
```
// устанавливаем в проект как прод-зависимость
npm i react-bootstrap bootstrap
```
```javascript
// импортируем сущности в модуль компонента
import { Container, Row, Col } from 'react-bootstrap';
import Button from 'react-bootstrap/button';
```

Используем внутри компонента:  
```
// Дает привычные элементы из `bootstrap-классов` в виде `react-компонентов`
// Модифицируются не специальными классами, а атрибутами компонентов

const someComp = () => {
  return (
    <Container>
      <Row>
        <Col> <Button variant="primary" disabled /> </Col>
      </Row>
    </Container>
  )
}
```

<br>

### Другие библиотеки
1.  [ReactStrap](https://reactstrap.github.io/?path=/story/home-installation--page)
2.  [Ant Design](https://ant.design/)
3.  [Material Design MUI](https://mui.com/)
4.  []()
