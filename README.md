import React, { Component } from 'react';
import './App.css';

class App extends Component {
  constructor() {
    super();
    this.state = {
      input: '',
      result: '',
    };
  }

  handleButtonClick = (value) => {
    if (value === 'C') {
      // Clear the input and result
      this.setState({ input: '', result: '' });
    } else if (value === '=') {
      try {
        // Evaluate the expression
        const evalResult = eval(this.state.input);
        this.setState({ result: evalResult });
      } catch (error) {
        this.setState({ result: 'Error' });
      }
    } else {
      // Append the value to the input
      this.setState((prevState) => ({ input: prevState.input + value }));
    }
  };

  render() {
    return (
      <div className="App">
        <h1>Arithmetic Calculator</h1>
        <div className="calculator">
          <div className="display">
            <input type="text" value={this.state.input} readOnly />
            <span className="result">{this.state.result}</span>
          </div>
          <div className="buttons">
            <div className="row">
              <button onClick={() => this.handleButtonClick('1')}>1</button>
              <button onClick={() => this.handleButtonClick('2')}>2</button>
              <button onClick={() => this.handleButtonClick('3')}>3</button>
              <button onClick={() => this.handleButtonClick('+')}>+</button>
            </div>
            <div className="row">
              <button onClick={() => this.handleButtonClick('4')}>4</button>
              <button onClick={() => this.handleButtonClick('5')}>5</button>
              <button onClick={() => this.handleButtonClick('6')}>6</button>
              <button onClick={() => this.handleButtonClick('-')}>-</button>
            </div>
            <div className="row">
              <button onClick={() => this.handleButtonClick('7')}>7</button>
              <button onClick={() => this.handleButtonClick('8')}>8</button>
              <button onClick={() => this.handleButtonClick('9')}>9</button>
              <button onClick={() => this.handleButtonClick('*')}>*</button>
            </div>
            <div className="row">
              <button onClick={() => this.handleButtonClick('C')}>C</button>
              <button onClick={() => this.handleButtonClick('0')}>0</button>
              <button onClick={() => this.handleButtonClick('=')}>=</button>
              <button onClick={() => this.handleButtonClick('/')}>/</button>
            </div>
          </div>
        </div>
      </div>
    );
  }
}

export default App;
