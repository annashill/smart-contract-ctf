# Smart Contract CTF

Plataforma de retos (*wargame*) para aprender **seguridad de contratos inteligentes en Ethereum**. Los usuarios se registran con su wallet, estudian contratos en Solidity con vulnerabilidades intencionales y los explotan o corrigen para sumar puntos.

> Proyecto semestral de **Criptografía**, Facultad de Ingeniería de Sistemas Computacionales, Universidad Tecnológica de Panamá.
> Construido sobre [**level_up!** de Telefónica](https://github.com/Telefonica/level_up) (AGPL-3.0).

## Stack

| Capa | Tecnología |
|---|---|
| Backend | Python 3.10 · Flask · Web3.py |
| Contratos | Solidity |
| Blockchain local | Ganache |
| Frontend | Plantillas Jinja + JavaScript (conexión con wallet) |
| Despliegue | Docker · Docker Compose |

## Retos incluidos

| # | Reto | Dificultad | Puntos |
|---|---|:-:|:-:|
| 0 | Interact | 0 | 25 |
| 1 | Questions | 1 | 50 |
| 2 | Ownership | 3 | 100 |
| 3 | Safeguarding | 2 | 75 |
| 4 | Origin | 3 | 150 |
| 5 | Relottery | 4 | 250 |
| 6 | Overworld | 3 | 100 |
| 7 | Blockchain Tour | 2 | 75 |
| 8 | Snippet Delegated | 4 | 200 |
| 9 | Rich Club | 5 | 250 |
| 10 | Deny To Me | 4 | 200 |
| 11 | Forensic Ouch | 3 | 150 |
| 12 | Replay Me | 5 | 250 |
| 13 | Guess my number | 4 | 200 |
| 14 | Pay me | 1 | 50 |
| 15 | Dex knowledge | 3 | 150 |
| 16 | Gas knowledge | 2 | 75 |
| 17 | Send to me | 3 | — |

Los contratos están en [`contracts/`](contracts/).

## Ejecutar con Docker

```bash
docker compose up --build
```

- Plataforma: http://localhost:5000
- Nodo Ganache: http://localhost:8545

> La clave privada de `compose.yaml` es una cuenta de prueba de Ganache. **Nunca uses claves reales** en este proyecto.

### Conectar MetaMask

Para jugar necesitas [MetaMask](https://metamask.io/) conectado a la red local de Ganache:

| Campo | Valor |
|---|---|
| Nombre de la red | Ganache Local |
| URL de RPC | `http://localhost:8545` |
| Chain ID | `1337` |
| Símbolo | ETH |

Si reinicias el contenedor de Ganache, la blockchain empieza vacía. En ese caso, borra `contract-address.json` dentro del contenedor de la app (o recrea ambos con `docker compose down && docker compose up`) para que los contratos se vuelvan a desplegar.

## Ejecutar en local

Requisitos: Python 3.9 o 3.10 y Ganache (CLI o GUI).

1. Crea un archivo `.env` en la raíz (ver [README_upstream_es.md](README_upstream_es.md#variables-del-entorno)).
2. Instala las dependencias y levanta Flask:

```bash
pip install -r requirements.txt
flask run
```

## Estructura

```
contracts/     Contratos Solidity de cada reto
templates/     Vistas HTML de los retos
static/        CSS, JS e imágenes
dapp.py        Aplicación Flask
functions.py   Lógica de despliegue y verificación en la blockchain
docs/          Documentación del proyecto
```

## Roadmap

- [ ] Levantar la plataforma con Docker y documentar la configuración
- [ ] Documentar cada reto: vulnerabilidad, explotación y corrección
- [ ] Agregar retos propios (p. ej., reentrada y DoS por gas)
- [ ] Reportes de progreso por usuario

## Créditos y licencia

Basado en [level_up!](https://github.com/Telefonica/level_up) de Telefónica Innovación Digital. La documentación original está en [README_upstream.md](README_upstream.md) y [README_upstream_es.md](README_upstream_es.md).

Este proyecto se distribuye bajo la licencia **GNU AGPL-3.0**, igual que el original. Consulta [LICENSE](LICENSE).
