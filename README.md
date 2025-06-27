# Bienestar-programa
Jugando con Python haciendo un programa de bienestar

import datetime

def registrar_dia():
    fecha = datetime.datetime.now().strftime("%d/%m/%Y")
    print(f"\n🌞 Bitácora del día {fecha}")

    estado_animo = input("¿Cómo te sientes hoy? (Ej: feliz, cansada, animada): ")
    energia = input("Nivel de energía (1 al 10): ")
    horas_sueno = input("¿Cuántas horas dormiste?: ")
    emociones = input("Escribe 3 emociones que hayas sentido hoy (separadas por coma): ")
    afirmacion = input("Escribe una afirmación positiva para ti hoy: ")

    print("\n¿Cumpliste con estos hábitos hoy?")
    agua = input("💧 Tomaste suficiente agua (s/n): ").lower()
    ejercicio = input("🏃‍♀️ Hiciste algo de actividad física (s/n): ").lower()
    meditacion = input("🧘‍♀️ Meditaste o te desconectaste un rato (s/n): ").lower()
    amor_propio = input("❤️ Te hablaste con amor a ti misma (s/n): ").lower()

    entrada = f"""{fecha};{estado_animo};{energia};{horas_sueno};{emociones};{afirmacion};{agua};{ejercicio};{meditacion};{amor_propio}\n"""

    with open("bitacora_bienestar.csv", "a", encoding="utf-8") as archivo:
        archivo.write(entrada)
    
    print("\n🌼 ¡Entrada guardada! Gracias por cuidarte hoy.")

def ver_entradas():
    print("\n📖 Entradas anteriores:")
    try:
        with open("bitacora_bienestar.csv", "r", encoding="utf-8") as archivo:
            for linea in archivo:
                datos = linea.strip().split(";")
                print(f"{datos[0]} | Ánimo: {datos[1]}, Energía: {datos[2]}, Sueño: {datos[3]}h, Emociones: {datos[4]}")
    except FileNotFoundError:
        print("❌ Aún no hay registros. Comienza hoy 🌱")

def mostrar_menu():
    print("\n🌿 BITÁCORA DE BIENESTAR DIARIA 🌿")
    print("1. Registrar mi día")
    print("2. Ver entradas anteriores")
    print("3. Salir")

def main():
    while True:
        mostrar_menu()
        opcion = input("Elige una opción: ")
        if opcion == "1":
            registrar_dia()
        elif opcion == "2":
            ver_entradas()
        elif opcion == "3":
            print("🌙 Gracias por cuidarte hoy. Nos vemos mañana.")
            break
        else:
            print("⚠️ Opción inválida.")

main()
