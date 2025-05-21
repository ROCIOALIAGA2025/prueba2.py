import streamlit as st
import random

st.set_page_config(page_title="Aprende Python", page_icon="🐍", layout="centered")

st.title("🧠 Aprende Python - Control de Flujo")
st.markdown("""
Esta página te ayudará a entender cómo funcionan los bucles `while`, `for` y la estructura condicional `if` en Python.
""")

with st.expander("📘 Explicación de conceptos"):
    st.markdown("""
    - `if`: Permite ejecutar código condicionalmente.
    - `for`: Itera sobre una secuencia (listas, strings, rangos, etc).
    - `while`: Ejecuta un bloque de código mientras se cumpla una condición.
    """)

# Lista de preguntas
questions = [
    {
        "question": "¿Qué hace un bucle `for` en Python?",
        "options": [
            "Repite una acción hasta que sea falsa.",
            "Ejecuta código una sola vez.",
            "Itera sobre una secuencia de elementos."
        ],
        "answer": 2
    },
    {
        "question": "¿Cuál es la salida de: for i in range(3): print(i)?",
        "options": ["0 1 2", "1 2 3", "0 1 2 3"],
        "answer": 0
    },
    {
        "question": "¿Qué hace el siguiente código?\n\nx = 0\nwhile x < 3:\n  print(x)\n  x += 1",
        "options": ["Imprime 0 1 2", "Imprime 1 2 3", "Error de sintaxis"],
        "answer": 0
    },
    {
        "question": "¿Cuál es el operador de comparación correcto para igualdad?",
        "options": ["=", "==", "==="],
        "answer": 1
    },
    {
        "question": "¿Qué palabra clave detiene un bucle `for` antes de que termine?",
        "options": ["stop", "exit", "break"],
        "answer": 2
    },
    {
        "question": "¿Qué hace `continue` en un bucle?",
        "options": [
            "Termina el bucle inmediatamente.",
            "Salta a la siguiente iteración.",
            "Reinicia todo el programa."
        ],
        "answer": 1
    },
    {
        "question": "¿Cuál es la salida?\n\nx = 5\nif x > 3:\n  print(\"Mayor\")",
        "options": ["Error", "Mayor", "Nada"],
        "answer": 1
    },
    {
        "question": "¿Cuál es la salida de `range(2, 5)`?",
        "options": ["2 3 4", "2 3 4 5", "3 4 5"],
        "answer": 0
    },
    {
        "question": "¿Qué hace `else` en un bloque `if`?",
        "options": [
            "Se ejecuta si el `if` es falso.",
            "Repite código varias veces.",
            "Detiene el programa."
        ],
        "answer": 0
    },
    {
        "question": "¿Qué palabra inicia un bloque condicional?",
        "options": ["for", "while", "if"],
        "answer": 2
    },
]

st.markdown("### 📝 Responde el cuestionario:")

score = 0
user_answers = []

for i, q in enumerate(questions):
    st.write(f"**{i+1}. {q['question']}**")
    user_answer = st.radio(f"Pregunta {i+1}", q["options"], key=i)
    user_answers.append(q["options"].index(user_answer))

if st.button("🎯 Calcular puntaje"):
    for i, answer in enumerate(user_answers):
        if answer == questions[i]["answer"]:
            score += 1
    st.success(f"Tu puntaje es: {score} / {len(questions)}")

    if score == len(questions):
        st.balloons()
