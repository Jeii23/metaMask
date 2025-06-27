# MetaMask Webapp

Una petita aplicació web que permet **enviar transaccions Ethereum *sense signar* directament al teu MetaMask** a partir d’un fragment JSON enganxat a la pàgina web. Està pensada com a recurs educatiu i de prova per entendre el flux de preparació i signatura de transaccions abans d’enviar‑les a la xarxa.

## ✨ Funcionalitats

* **Conversió ASCII → Hex**: detecta automàticament cadenes de text en el camp `data` i les codifica a hexadecimal perquè siguin vàlides com a calldata EVM.
* **Integració MetaMask**: fa servir l’API `ethereum.request` per demanar permís, seleccionar compte i cridar `eth_sendTransaction`.
* **Servidor Express minimalista**: només serveix contingut estàtic (`public/`) perquè puguis desplegar‑lo fàcilment a qualsevol servei Node.js o fins i tot com a *static hosting*.
* **Interfície en Català**: text i comentaris en el codi pensats per a la comunitat catalanoparlant.

## 📂 Estructura del projecte

```
metamask-webapp/
├── app.js              # Servidor Express
├── package.json        # Dependències i scripts npm
├── public/
│   ├── index.html      # UI principal
│   └── script.js       # Lògica de client (MetaMask)
└── node_modules/       # 📦 (generat per npm install)
```

## ⚙️ Requisits

| Programari   | Versió recomanada                        |
| ------------ | ---------------------------------------- |
| **Node.js**  | ≥ 18.x                                   |
| **npm**      | ≥ 9.x                                    |
| **MetaMask** | Última versió de l’extensió al navegador |

> 💡 **Nota**: llicència ISC; pots usar el projecte lliurement sempre que conservis l’avís de copyright.

## 🚀 Instal·lació i execució local

```bash
# 1. Clona el repositori
git clone <url-del-repo>
cd metamask-webapp

# 2. Instal·la dependències
npm install

# 3. (Opcional) afegeix un script start
npm set-script start "node app.js"

# 4. Engega el servidor
npm start
# —o—
node app.js
```

El servidor escoltarà per defecte al **port 4000** (o al que defineixis a la variable d’entorn `PORT`).

Obre `http://localhost:4000` al teu navegador amb MetaMask instal·lat i segueix les instruccions de la pàgina.

## 🧑‍💻 Ús

1. Enganxa un JSON de transacció **sense signar** al camp de text.
2. Fes clic a **“Enviar Transacció a MetaMask”**.
3. MetaMask et demanarà:

   * Connectar el compte (si encara no ho has fet).
   * Revisar i **signar** la transacció.
4. Un cop signada, MetaMask la retransmetrà a la xarxa seleccionada.

### Exemple de JSON mínim

```json
{
  "from": "0xElTeuCompte",
  "to": "0xReceptorAddress1234567890abcdef",
  "value": "0x9184e72a000",
}
```

