import streamlit as st
import random

# Título
st.title("Aprende Python: Bucles y Condicionales")
st.markdown("## 🐍 Estructuras de Control: `while`, `for`, `if`")

# Explicación básica
with st.expander("📘 Explicación rápida"):
    st.markdown("""
    ### 🔁 Bucle `while`
    Ejecuta un bloque de código **mientras** se cumpla una condición.

    ```python
    x = 0
    while x < 5:
        print(x)
        x += 1
    ```

    ### 🔁 Bucle `for`
    Itera sobre una secuencia (lista, string, rango, etc.).

    ```python
    for i in range(5):
        print(i)
    ```

    ### 🔀 Condicional `if`
    Ejecuta código si se cumple una condición.

    ```python
    x = 10
    if x > 5:
        print("Mayor que 5")
    elif x == 5:
        print("Es 5")
    else:
        print("Menor que 5")
    """)

# Preguntas
st.markdown("## 📝 Cuestionario")
preguntas = [
    {
        "pregunta": "¿Cuál es la palabra clave para un bucle que se repite mientras se cumpla una condición?",
        "opciones": ["for", "while", "if"],
        "respuesta": "while"
    },
    {
        "pregunta": "¿Qué hace `range(3)`?",
        "opciones": ["[0, 1, 2]", "[1, 2, 3]", "[0, 1, 2, 3]"],
        "respuesta": "[0, 1, 2]"
    },
    {
        "pregunta": "¿Qué se imprime?\n```python\nx = 3\nif x > 2:\n    print('Sí')\n```",
        "opciones": ["No", "Sí", "Error"],
        "respuesta": "Sí"
    },
    {
        "pregunta": "¿Qué hace este código?\n```python\nfor i in range(2):\n    print(i)\n```",
        "opciones": ["Imprime 0 y 1", "Imprime 1 y 2", "No imprime nada"],
        "respuesta": "Imprime 0 y 1"
    },
    {
        "pregunta": "¿Qué estructura se usa para múltiples condiciones?",
        "opciones": ["for", "if/elif/else", "while"],
        "respuesta": "if/elif/else"
    },
    {
        "pregunta": "¿Qué se imprime?\n```python\nx = 0\nwhile x < 3:\n    x += 1\nprint(x)\n```",
        "opciones": ["0", "2", "3"],
        "respuesta": "3"
    },
    {
        "pregunta": "¿Cuál estructura se usa comúnmente para recorrer listas?",
        "opciones": ["while", "if", "for"],
        "respuesta": "for"
    },
    {
        "pregunta": "¿Qué hace este código?\n```python\nx = 5\nif x == 5:\n    print('Correcto')\n```",
        "opciones": ["Imprime 'Correcto'", "Error", "No imprime nada"],
        "respuesta": "Imprime 'Correcto'"
    },
    {
        "pregunta": "¿Qué operador se usa para comparar igualdad?",
        "opciones": ["=", "==", "!="],
        "respuesta": "=="
    },
    {
        "pregunta": "¿Qué tipo de bucle es ideal si no sabes cuántas veces se repetirá?",
        "opciones": ["for", "while", "if"],
        "respuesta": "while"
    }
]

respuestas_usuario = []
puntaje = 0

# Mostrar preguntas
for i, q in enumerate(preguntas):
    seleccion = st.radio(q["pregunta"], q["opciones"], key=f"pregunta_{i}")
    respuestas_usuario.append(seleccion)

# Botón para corregir
if st.button("🎯 Ver Puntaje"):
    puntaje = sum(
        1 for i, r in enumerate(respuestas_usuario)
        if r == preguntas[i]["respuesta"]
    )
    st.success(f"Tu puntaje: {puntaje} / {len(preguntas)}")

    if puntaje == len(preguntas):
        st.balloons()
    elif puntaje >= 7:
        st.info("¡Muy bien! Puedes repasar para perfeccionar.")
    else:
        st.warning("Sigue practicando. ¡Tú puedes!")

