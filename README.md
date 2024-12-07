# calc-peso
import image from "./assets/workout-animate.svg"
import { FaWeightHanging } from "react-icons/fa6"
import{FaRuler} from "react-icons/fa";
import { useState } from "react";
function App() {
 const [peso, setPeso] = useState(0)
const [altura,SetAltura] = useState(0)
const [loading, setLoading] = useState(false);
const [resultado, setResultado] = useState("");

function clickCalcular(){
  setLoading(true)
const valorImc = peso / (altura * altura)
setResultado(valorImc.toFixed(2))
console.log(valorImc)

setTimeout(
  () => {setLoading(false)
  }, 1500
  )

}
  return (
    <div className="w-full h-screen flex bg-green-600">
      <div className="w-[50%] h-full flex items-center justify-content">
        <img src={image} alt="" width={750} />
      </div>
      <div className="w-[50%] h-full flex items-center justify-center">
        <div className="w-[60%] h-auto p-[20px] rounded-lg flex flex-col bg-[#1f1f1f1f]">
          <div className="w-full flex flex-col">
            <h1 className="text-white text-[40px] font-bold">Calculadora - IMC
            </h1>
            <div className="w-[250px] h-[4px] rounded-lg bg-black"></div>
          </div>
          <div className="w-full flex flex-col ">
            <div className="mt-4">
              <label htmlFor="" className="text-white text-[18px]">peso</label>
              <div className="w-full flex bg-[#555555] h-[40px]">
                <div className="w-[10%] h-full flex  items-center justify-center">
                  <FaWeightHanging size={24} color="#B0B0B0FF rounded-md h-[50px]" />
                </div>
                <div className="w-[80%] h-full ">
                  <input className="w-full h-full bg-transparent border-none outline-none text-white" type="number"
                  onChange={
                    (event)=> setPeso(event.target.value)
                  }
                  />
                </div>
                <div className="w-[10%] h-full flex items-center justify-center">
                  <p className="">Kg</p>
                </div>
              </div>
            </div>
            <div className="mt-4">
              <label htmlFor="" className="text-white text-[18px]">Altura</label>
              <div className="w-full flex bg-[#555555] h-[40px]">
                <div className="w-[10%] h-full flex  items-center justify-center">
                  <FaRuler size={24} color="#B0B0B0FF rounded-md h-[50px]" />
                </div>
                <div className="w-[80%] h-full ">
                  <input className="w-full h-full bg-transparent border-none outline-none text-white" type="number" 
                  onChange= {
                    (event) => SetAltura(event.target.value)
                  }
                  />
                </div>
                <div className="w-[10%] h-full flex items-center justify-center">
                  <p className="">M</p>
                </div>
              </div>
            </div>
          </div>
          <div className="fim">
           <div className="w-full flex flex-col items-center justify-center ">
            <button className="mt-[30px] w-full h-[40px] bg-[#20a54c] rounded-lg text-white font-bold"
            onClick={clickCalcular}>
              {
                loading ? (
                 <div className="w-full h-full flex items-center justify-center">
                   <div className="
                  w-[30px] h-[30px] border-2 border-t-[4px] border-white rounded-full animate-spin"></div>
                 </div>
                ) : "Calcular"
              }
            </button>
           </div>
           {
            resultado && (
              <div className=" w-full flex justify-center flex-col">
                <div className="w-full bg-gray-500 h-[1px] mt-4"></div>
                <div className="w-full py-4 flex">
                  <div className="w-[20%] flex flex-col items-center justify-center">
                   <p className="text-[30px] text-[#f03333]">{resultado}</p>    
                   <p className="text-[18px] text-white">Seu IMC</p>                  
                  </div>
                  <div className="w-[80%] flex items-center justify-center">
                    <p className="text-[20px] text-white">Seu Peso está ideal</p>
                  </div>
                </div>
                <div className="w-full bg-gray-500 h-[1px] mt-4"></div>
                <div className="w-full flex item-center justify-center">
                  <a className="decoration-[0] text-[20px] text-[#f03333] mt-4" href=""> Mais inforações sobre o IMC</a>
                </div>
              </div>
            )
           }
          </div>

        </div>
      </div>
    </div>
  )
}

export default App



@tailwind base;
@tailwind components;
@tailwind utilities;

/** @type {import('tailwindcss').Config} */
export default {
  content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}

import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

// https://vite.dev/config/
export default defineConfig({
  plugins: [react()],
})
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="/vite.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Vite + React</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.jsx"></script>
  </body>
</html>

