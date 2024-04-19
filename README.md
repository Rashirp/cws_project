// App.js

import Joke from "./components/Joke";

function App() {
	return (
		<div className="App">
			<h1>Joke Generator Using React and Joke API</h1>
			<Joke/>
		</div>
	);
}

export default App;

// Joke.js

import React from "react";

import Button from "./Button";
import './Joke.css';

const Joke = () => {
	const [Joke, setJoke] = React.useState("");

	const fetchApi = () => {
		fetch("https://sv443.net/jokeapi/v2/joke/Programming?type=single")
			.then((res) => res.json())
			.then((data) => setJoke(data.joke));
	};

	return (
		<div className="joke">
			<Button callApi={fetchApi} /> 
			<p>{Joke}</p> 
		</div>
	);
}

export default Joke;

/* Joke.css */

body {
	background-color: rgb(47, 97, 80);
}

.joke {
	width: auto;
	height: auto;
	margin: auto;
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: center;
	color: beige;
}

h1 {
	text-align: center;
	color: beige;
}

// Button.js

import React from "react";
import './Button.css'

const Button = (props) => {
	return <button onClick={props.callApi}>
		Click to generate a joke.
	</button>;
}

// Export Button Component
export default Button;

/* Button.css */

button {
	display: inline-block;
	padding: 10px 20px;
	background-color: #70a03a;
	color: #ffffff;
	border: none;
	font-size: 16px;
	cursor: pointer;
	border-radius: 8px;
	transition: background-color .5s;
}

button:hover {
	background-color: #c1f590;
}

button:active {
	background-color: #297910;
}
