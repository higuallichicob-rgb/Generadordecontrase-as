# Generadordecontraseñas

import tkinter as tk
import random
import string

def generar_contraseña():
    """Genera una contraseña segura con mayúsculas, minúsculas, números y símbolos."""

try:
        # Obtener la longitud ingresada por el usuario
        longitud = int(entry_longitud.get())
    except ValueError:
        resultado.set("Ingresa un número válido")
        return

if longitud < 5:
        resultado.set("Mínimo 5 caracteres")
        return

 # Conjuntos de caracteres
mayusculas = string.ascii_uppercase
minusculas = string.ascii_lowercase
 numeros = string.digits
 simbolos = string.punctuation

# Lista para almacenar los caracteres seleccionados
contraseña = [
        random.choice(mayusculas),  # Al menos una mayúscula
        random.choice(minusculas), # Al menos una minúscula
        random.choice(numeros),    # Al menos un número
        random.choice(simbolos)    # Al menos un símbolo
    ]

# Usamos un bucle for para rellenar el resto de la contraseña
 todos = mayusculas + minusculas + numeros + simbolos
    for _ in range(longitud - 5):
        contraseña.append(random.choice(todos))

  # Mezclar para evitar un patrón predecible
 random.shuffle(contraseña)

 # Unir la lista en un string y mostrarlo
 resultado.set(''.join(contraseña))


ventana = tk.Tk()
ventana.title("🔐 Generador de Contraseñas")
ventana.geometry("400x250")
ventana.configure(bg="#2c3e50") 

tk.Label(ventana, text="Tamaño de la contraseña:").pack()
entry_longitud = tk.Entry(ventana)
entry_longitud.pack()

tk.Button(ventana, text="Crear", command=generar_contraseña).pack()

resultado = tk.StringVar()
tk.Label(ventana, textvariable=resultado, font=("Arial", 14), fg="blue").pack()

ventana.mainloop()
