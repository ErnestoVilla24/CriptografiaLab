// ==UserScript==
// @name         New Userscript
// @namespace    http://tampermonkey.net/
// @version      0.1
// @description  try to take over the world!
// @author       You
// @match        https://cripto.tiiny.site/
// @require      https://cdnjs.cloudflare.com/ajax/libs/crypto-js/4.2.0/crypto-js.min.js#sha512-a+SUDuwNzXDvz4XrIcXHuCf089/iJAoN4lmrXJg18XnduKK6YlDHNRalv4yd1N40OKI80tFidF+rqTFKGPoWFQ==
// @icon         https://www.google.com/s2/favicons?sz=64&domain=tiiny.site
// @grant        none
// ==/UserScript==

(function() {
    'use strict';

     function decodificador(mensajes, letrasMayusculas) {

        // Decodificar el mensaje cifrado en base64
        const ciphertext = CryptoJS.enc.Base64.parse(mensajes);

        // Convertir la clave de texto plano a formato WordArray
        const keyBytes = CryptoJS.enc.Utf8.parse(letrasMayusculas);

        // Configurar los parámetros del algoritmo 3DES
        const options = { mode: CryptoJS.mode.ECB, padding: CryptoJS.pad.Pkcs7 };

        // Descifrar el mensaje utilizando 3DES
        const decrypted = CryptoJS.TripleDES.decrypt(
            { ciphertext: ciphertext },
            keyBytes,
            options
        );

        // Devolver el mensaje descifrado como una cadena de texto
        return decrypted.toString(CryptoJS.enc.Utf8);
    }

    // Obtén el texto dentro del elemento <p>
    var parrafo = document.querySelector('p');
    if (parrafo) {
        var texto = parrafo.textContent;

        // Define la expresión regular para buscar letras mayúsculas
        var patron = /[A-Z]/g;

        // Busca el patrón en el texto
        var coincidencias = texto.match(patron);

        // Si se encuentran coincidencias
        if (coincidencias) {
            // Muestra las letras mayúsculas en la consola
            var letrasMayusculas = coincidencias.join('');
            console.log("La llave es: " + letrasMayusculas);

        }
    }

        // Obtiene todos los elementos con atributo "id"
    var Ids = document.querySelectorAll('[id]');

    // Imprime el mensaje con la cantidad de elementos encontrados
    console.log("Los mensajes cifrados son: " + Ids.length);

    Ids.forEach((Id) => {
        const mensaje = decodificador(Id.id, letrasMayusculas)
        console.log(Id.id + " " + mensaje)
        const div = document.createElement("div");
        div.textContent = mensaje;
        document.body.appendChild(div);
    });


})();
