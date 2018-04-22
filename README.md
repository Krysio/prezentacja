# React.js

Biblioteka JavaScript (nie framework)

Jest to biblioteka służąca do tworzenia dynamicznych interfejsów użytkownika. I nic poza tym.

Zalety:
- deklaratywność
- VirtualDOM
- szybki (szybszy od Angulara)
- czytelny

Wady:
- JSX = Babel

### Historia

Napisany w 2009r przez Jordana Walke, programisetę FaceBook'a

Datay:
- Od października 2014r – udostępniona na 3-klauzulowej licencja BSD wraz z dodatkiem patentowym
- Od września 2017 – od wersji 16.0 Reacj.js udostępniany jest na licencji MIT
- Styczeń 2015r – Pierwsza wersja React Native
- Kwiecień 2017r – Pierwsza wersja React VR

### Podział na conajmniej 2 biblioteki

**Przeglądarka**
- React.js
- React DOM

**Android**
- React.js
- React Native

**VR**
- React.js
- React VR

#### Przepływ danych

[![N|Solid](https://sirius.cs.put.poznan.pl/~inf108589/images/flux-diagram.png)](https://nodesource.com/products/nsolid)

### Cykl życia komponentu

[![N|Solid](https://sirius.cs.put.poznan.pl/~inf108589/images/cykle-zycia.png)](https://nodesource.com/products/nsolid)

## Przykłady

### W przegląrce

```html
<!DOCTYPE html>
<html lang="pl">
  <head>
    <meta charset="UTF-8">
    <title>Pierwszy komponent w React.js</title>
    <script src="https://unpkg.com/react/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom/umd/react-dom.development.js"></script>
    <script src="https://unpkg.com/babel-standalone/babel.js"></script>
  </head>
  <body>
    <div id="app"></div>
    <script type="text/babel">
      ReactDOM.render(
        <h1>Hello world!</h1>,
        document.getElementById('app')
      );
    </script>
  </body>
</html>
```

### Przykład komponentu

```jsx
class DateComponent extends React.Component {
  constructor(props) {
    super(props);

    this.state = {
      date: new Date()
    };
  }

  componentDidMount() {
    this.timerId = window.setInterval(this.updateDate.bind(this), 1000);
  }

  componentWillUnmount() {
    window.clearInterval(this.timerId);
  }

  updateDate() {
    this.setState({
      date: new Date()
    });
  }

  render() {
    const dateStr = this.state.date.toString();
    return <time>{dateStr}</time>;
  }
}
```

```jsx
ReactDOM.render(
  <App />,
  document.getElementById("app")
);
```

### Aktualizacja widoku

**setState**
```jsx
constructor(props) {
  this.state = {
    property: 'value'
  };
}
render() {
  return <pre>{ this.stete.property }</pre>;
}
```
`setState(obejctUpdater[, callback])`
```jsx
onAction() {
  this.setState({
    property: 'foo';
  });
}
```
`setState(stateChange[, callback])`
```jsx
this.setState((prevState, props) => {
  return {property: prevState.property + props.value};
});
```
**forceUpdate**
```jsx
onAction() {
  this.forceUpdate();
}
render() {
  return <pre>{ data.getValue() }</pre>
}
```
`forceUpdate([callback])`

### Props, refs (parametry)

```jsx
  render () {
    return (
      <Modal ref="modal" title={prompt.title} footer={this.renderFooter}>
        <div class="my-prompt form-group">
          <textarea 
            class="form-control" 
            type="text" 
            value={prompt.text} 
            onChange={this.onChange} 
            />
        </div>
      </Modal>
    );
  }

  renderFooter () {
    return (
      <div class="modal-footer">
        <div class="btn-group my-flex-end">
          <button class="btn btn-primary" onClick={this.onSubmit}>Submit</button>
          <button class="btn btn-default" onClick={this.onCancel}>Cancel</button>
        </div>
      </div>
    )
  }
```
```jsx
  render () {
    return (
      <canvas 
        ref={this.setCanvasElement}
        onMouseDown={this.onMouseDown}
        onMouseUp={this.onMouseUp}
        onMouseMove={this.onMouseMove}
        onMouseLeave={this.onMouseLeave}
        onWheel={this.onWheel}
        onClick={this.onClick}
      />
    );
  }
```
```jsx
componentDidMount () {
  this.refs[ name ];
  this.props[ name ];
}
```
