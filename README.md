# ParcialFrontEnd3
//Este es el primer parcial de front end 3 de la camada 9


import "./App.css";
import { useState } from "react";
import FormInput from "./Components/FormInput";

const App = () => {
  const [values, setValues] = useState({
    username: "",
    favoritecolor:"",
  });

  const inputs = [
    {
      id: 1,
      name: "username",
      type: "text",
      placeholder: "Ingresa tu nombre",
      errorMessage:
        "Username should be 3-16 characters and shouldn't include any special character!",
      label: "Username",
      pattern: "^[A-Za-z0-9]{3,16}$",
      required: true,
    },
    {
      id: 2,
      name: "favorite color",
      type: "favorite color",
      placeholder: "Ingresa tu color favorito",
      errorMessage: "Please enter a color!",
      label: "favorite color",
      required: true,
    },
  ];

  const handleSubmit = (e) => {
    e.preventDefault();
  };

  const onChange = (e) => {
    setValues({ ...values, [e.target.name]: e.target.value });
  };

  return (
    <div className="app">
      <form onSubmit={handleSubmit}>
        <h1>Register</h1>
        {inputs.map((input) => (
          <FormInput
            key={input.id}
            {...input}
            value={values[input.name]}
            onChange={onChange}
          />
        ))}
        <button>Submit</button>
      </form>
    </div>
  );
};

export default App;
