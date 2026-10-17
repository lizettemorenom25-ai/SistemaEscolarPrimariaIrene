# Sistema Escolar Primaria Irene

## Descripción del proyecto

El Sistema Escolar Primaria Irene es una aplicación desarrollada en Python que permite administrar información básica de estudiantes de una escuela primaria. El programa utiliza el paradigma de Programación Orientada a Objetos (POO) para organizar el código mediante clases, atributos y métodos.

## Objetivo

Desarrollar una aplicación sencilla que permita registrar, consultar, buscar y editar información de estudiantes, aplicando los conceptos fundamentales de la Programación Orientada a Objetos y las herramientas de desarrollo de software.

## Funcionalidades

- **Agregar estudiantes:** registra matrícula, nombre, edad y grado escolar.
- **Mostrar estudiantes:** presenta los datos de los estudiantes registrados.
- **Buscar estudiantes:** localiza un registro mediante la matrícula.
- **Editar estudiantes:** permite actualizar los datos de un estudiante.
- **Validar información:** comprueba que los datos sean válidos y evita matrículas duplicadas.
- **Menú interactivo:** facilita la navegación entre las opciones del sistema.

## Tecnologías utilizadas

- Python 3.
- Visual Studio Code.
- Git.
- GitHub.

## Estructura del proyecto

```text
SistemaEscolarPrimariaIrene/
├── sistema_escolar.py
└── README.md
```

## Requisitos

- Tener Python 3 instalado.
- Contar con el archivo `sistema_escolar.py`.

## Cómo ejecutar el programa

1. Descarga o clona este repositorio.
2. Abre la carpeta del proyecto en Visual Studio Code.
3. Abre una terminal.
4. Ejecuta el siguiente comando:

```bash
python sistema_escolar.py
```

Si el comando anterior no funciona en Windows, puedes probar:

```bash
py sistema_escolar.py
```

## Conceptos de programación aplicados

- Clases y objetos.
- Atributos y métodos.
- Constructor `__init__()`.
- Condicionales `if`, `elif` y `else`.
- Ciclo `while`.
- Ciclo `for`.
- Listas.
- Manejo de errores mediante `try` y `except`.
- Validación de datos.

## Alcances y limitaciones

El programa permite administrar registros durante la ejecución. Los datos se almacenan en una lista en memoria, por lo que los estudiantes agregados o modificados no se conservan al cerrar el programa. Para mantener la información de forma permanente, sería necesario incorporar una base de datos o almacenamiento en archivos.

## Conclusión

Este proyecto permitió poner en práctica los fundamentos de Python y la Programación Orientada a Objetos mediante una aplicación escolar sencilla y funcional. Su desarrollo también permitió utilizar Visual Studio Code para programar y GitHub para almacenar y controlar las versiones del código.
