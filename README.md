# CalculadoraDe_Propinas

Main.jsx
import React from "react";
import React from "react/dom-client";
import App from "./App";
import "./index.css";

ReactDOM.createRoot(document.getElementById("root")).render(
    <React.StrictMode>
        <App />
    </React.StrictMode>
);

App.jsx
import CalculadoraDePropinas from "./components/CalculadoraDePropinas";

function App() {
    return <CalculadoraDePropinas />
}

export default App;

Calculadora De Propinas.jsx
import { useState} from "react";
import Alerta from "/Alerta";

fuction CalculadoraDePropinas() {
    const [monto, setMonto] = useState("");
    const [porcentaje, setPorcentaje] = useState(15);
    const [propina, setPropina] = useState(null);
    const [total, setTotal] = useState(null);
    const [error, setError] = useState(null);

    const calcular = () => {
        setError("");
        setPropina(null);
        setTotal(null);

        if (monto.trim() === "") {
            setError(Debes ingresar el monto de la cuenta.);
            return;
        }

        const montoNumerico =parseFloat(monto);

        if (isNAN(montoNumerico) || montoNumerico <= 0) {
            setError("El monto mayor debe ser un numero mayor que 0.");
            return;
        }

        const valorPropina = montoNumerico * (porcentaje /100);
        consttotalFinal = montoNumerico + valorPropina;

        setPropina(valorPropina.toFixed(2));
        setTotal(totalFinal.tofixed(2));
    };

    return(
        <div className="min-h-screen bg-gray-100 flex items-center justify-center">
            <div className="bg-white p-8 rounded-2xl shadow-lg w-96">
                <h1 className="text-2xl font-bold text-center mb-6">
                    Calculadora De Propinas
                    </h1>

                    <label className="block m-2 font-semobold">
                        Total de la cuenta
                        </label>
                        <input
                        type= "text"
                        value={monto}
                        onChange={ (e) => setMonto(e.target.value)}
                        className="w-full p-2 border rounded-lg mb-4 focus:outline-none focus:ring-2 focus:ring-blue-400"
                        placeholder="Ej: 50.00"

                        />
                        <label className="block mb-2 font-semibold">
                            Selecciona el porcentaje
                            </label>
                            <select
                            value={porcentaje}
                            onChange={ (e) => setPorcentaje(parseInt(e.target.value))}
                            className="w-full p-2 border orunded-lg mb-4 focus:outline-none focus:ring-2 focus:ring-blue-400"

                            >

                            <option value={10}>10%</option>
                            <option value={15}>15%</option>
                            <option value={20}>20%</option>
                            </select>

                            <button 
                            onClick={calcular}
                            className="w-full bg-blue-500 text-white p-2 rounded-lg horver:bg-blue-600 transition"
                            >
                                Calcular
                            </button>

                            {error && <Alerta mensaje={error} />}

                            {propina && total && (
                                <div class name="mt-6 bg-green-100 p-4 rounded-lg text-center">
                                    <p className="font-semibold">Total a pagar: ${total}</p>
                                </div>
                            )}
                            </div>
                            :/div>
                            
    )
}

CodigoCompleto.jsx
import { useState} from "react";

function App() {
    const [monto, setMonto]= useState("");
    const [porcentaje, setPorcentaje]= useState(15);
    const [propina, setPropina]= useState(null);
    const [total, setTotal]= useState(null);
    const [mensajeerror, setMensajeError]= useState("");

    const Calculadora de propina =(e) => {
        e.preventDefault();
        setMensajeError("");
        setPropina(null);
        setTotal(null);

        //Las Validadciones
        if (monto.trim() === ""){
            setMensajeError("Por favor ingrese el monto de la cuenta.");
            return;
        }
        const montoNumerico = parseFloat(monto);

        if (isNaN(montoNumerico) || montoNumerico <= 0) {
            setMensajeError("El monto debe ser un numero valido mayor que 0.");
            return;
        }

        const valorPropina = montoNumerico * (porcentaje / 100);
        const totalFinal= montoNumerico + valorPropina;

        setPropina(valorPropina.toFixed(2));
        setTotal(totalFinal.toFixed(2));
    };

    return (
        <div className="min-h-screen b-gray-100 flex items-center justify-center">
            <div className="bg-white p-8 rounded-2xl shadow-lg w-96">
                <h1 className="text-2xl font-bold text-center mb-6">
                    calculadora de propinas
                </h1>

                <form onSubmit={calcularPropina}>
                    {/* Input del monto */}
                    <label className="block mb-2 font -semibold">
                        Total de la cuenta
                        </label>
                        <input
                        type="text"
                        value={monto}
                        onChange={(e) => setMonto(e.target.value)}
                        className="w-full p-2 border rounded-lg mb-4 focus:outline-none focus:ring-2 focus:ring-blue-400"
                        placeholder="Ej: 50.00"
                        >
                            /*Seleccion de porcentaje */{
                                <label className= "block mb-2 font-semibold"
                                Seleccione el porcentaje
                                </label>
                                <select
                                value={porcentaje}
                                onCahnge={(e) => setPorcentaje(parseInt(e.target.value))}
                                className="w-fullp-2 border rounded-lg mb-4 focus:outline-none focus:ring-2 focus:ring-blue-400"
                                   
                                <option value={10}>10%</option>
                                <option value={15}>15%</option>
                                <option value={20}>20%</option>
                                </select

                                <button
                                type="submit"
                                className="w-full bg-blue-500 text-white p-2 rounded-lg hover:bg-blue-600 transition"
                                >
                                    Calcular
                                </button>
                                </form>
                                {/* Alerta personalizada */}
                                {mensajeError && (
                                    <div className="mt-4 bg-red-100 text-red-700 p-3 rounded-lg text-center"
                                    {mensajeError}
                            </div>
                           )}

                           {/* Resultados */}
                           {propina && total && (
                            <div className="mt-6 bg-green-100 p-4 rounded-lg text-center">
                            <p className="font-semibold ">Propina: ${propina}</p>
                            <p className="font-semibold">Total a pagar: ${total}</p>
                            </div>
                        )}
                     </div>
                 </div>
              );

            }
                
