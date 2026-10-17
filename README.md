# SistemaEscolarPrimariaIrene
Sistema de gestión de estudiantes desarrollado en Python con POO.
# Clase Estudiante
class Estudiante:
    def __init__(self, matricula, nombre, edad, grado):
        if not isinstance(matricula, str) or not matricula.strip():
            raise ValueError("La matrícula no puede estar vacía.")

        if not isinstance(nombre, str) or not nombre.strip():
            raise ValueError("El nombre no puede estar vacío.")

        if not isinstance(edad, int) or isinstance(edad, bool) or edad <= 0:
            raise ValueError("La edad debe ser un entero mayor que cero.")

        if not isinstance(grado, str) or not grado.strip():
            raise ValueError("El grado no puede estar vacío.")

        self.matricula = matricula.strip()
        self.nombre = nombre.strip()
        self.edad = edad
        self.grado = grado.strip()

    # Mostrar información del estudiante
    def mostrar_info(self):
        print(f"Matrícula: {self.matricula}")
        print(f"Nombre: {self.nombre}")
        print(f"Edad: {self.edad}")
        print(f"Grado: {self.grado}")
        print("-" * 30)


# Clase Escuela
class Escuela:
    def __init__(self, nombre):
        if not isinstance(nombre, str) or not nombre.strip():
            raise ValueError("El nombre de la escuela no puede estar vacío.")

        self.nombre = nombre.strip()
        self.estudiantes = []

    # Buscar estudiante por matrícula
    def buscar_estudiante(self, matricula):
        matricula = matricula.strip().casefold()

        for est in self.estudiantes:
            if est.matricula.casefold() == matricula:
                return est

        return None

    # Agregar estudiante
    def agregar_estudiante(self, estudiante):
        if not isinstance(estudiante, Estudiante):
            print("Error: el registro debe ser un objeto Estudiante.")
            return False

        if self.buscar_estudiante(estudiante.matricula):
            print(
                f"Error: la matrícula {estudiante.matricula} "
                "ya está registrada."
            )
            return False

        self.estudiantes.append(estudiante)
        print(f"Estudiante {estudiante.nombre} agregado correctamente.")
        return True

    # Mostrar todos los estudiantes
    def mostrar_estudiantes(self):
        print(f"\nEstudiantes de {self.nombre}")

        if not self.estudiantes:
            print("No hay estudiantes registrados.")
            return

        for est in self.estudiantes:
            est.mostrar_info()

    # Buscar y mostrar un estudiante
    def consultar_estudiante(self):
        matricula = input("Ingresa la matrícula del estudiante: ").strip()

        if not matricula:
            print("Error: debes ingresar una matrícula.")
            return

        estudiante = self.buscar_estudiante(matricula)

        if estudiante:
            print("\nEstudiante encontrado:")
            estudiante.mostrar_info()
        else:
            print("No se encontró un estudiante con esa matrícula.")

    # Editar los datos de un estudiante
    def editar_estudiante(self):
        matricula = input(
            "Ingresa la matrícula del estudiante que deseas editar: "
        ).strip()

        if not matricula:
            print("Error: debes ingresar una matrícula.")
            return

        estudiante = self.buscar_estudiante(matricula)

        if not estudiante:
            print("No se encontró un estudiante con esa matrícula.")
            return

        print("\nDatos actuales:")
        estudiante.mostrar_info()

        print("Deja un campo vacío si deseas conservar su valor actual.")

        nombre = input(f"Nuevo nombre [{estudiante.nombre}]: ").strip()
        edad_texto = input(f"Nueva edad [{estudiante.edad}]: ").strip()
        grado = input(f"Nuevo grado [{estudiante.grado}]: ").strip()

        # Validar y preparar los cambios antes de guardarlos
        nuevo_nombre = nombre if nombre else estudiante.nombre
        nuevo_grado = grado if grado else estudiante.grado

        if edad_texto:
            try:
                nueva_edad = int(edad_texto)
                if nueva_edad <= 0:
                    print("Error: la edad debe ser mayor que cero.")
                    return
            except ValueError:
                print("Error: la edad debe ser un número entero.")
                return
        else:
            nueva_edad = estudiante.edad

        # Guardar los cambios solo si los datos son válidos
        estudiante.nombre = nuevo_nombre
        estudiante.edad = nueva_edad
        estudiante.grado = nuevo_grado

        print("\nEstudiante actualizado correctamente.")
        estudiante.mostrar_info()


# Programa principal con menú
def main():
    escuela = Escuela("Primaria Irene")

    # Registros iniciales de ejemplo
    try:
        escuela.agregar_estudiante(
            Estudiante("PI001", "Ana", 10, "5to")
        )
        escuela.agregar_estudiante(
            Estudiante("PI002", "Luis", 11, "5to")
        )
    except ValueError as error:
        print(f"Error al registrar: {error}")
        return

    while True:
        print(f"\n===== SISTEMA ESCOLAR: {escuela.nombre} =====")
        print("1. Agregar estudiante")
        print("2. Mostrar estudiantes")
        print("3. Buscar estudiante")
        print("4. Editar estudiante")
        print("5. Salir")

        opcion = input("Selecciona una opción: ").strip()

        if opcion == "1":
            try:
                matricula = input("Matrícula: ").strip()
                nombre = input("Nombre: ").strip()
                edad = int(input("Edad: "))
                grado = input("Grado escolar: ").strip()

                estudiante = Estudiante(
                    matricula, nombre, edad, grado
                )
                escuela.agregar_estudiante(estudiante)

            except ValueError as error:
                print(f"Error en los datos: {error}")

        elif opcion == "2":
            escuela.mostrar_estudiantes()

        elif opcion == "3":
            escuela.consultar_estudiante()

        elif opcion == "4":
            escuela.editar_estudiante()

        elif opcion == "5":
            print("Gracias por utilizar el sistema escolar.")
            break

        else:
            print("Opción no válida. Intenta nuevamente.")


# Punto de entrada
if __name__ == "__main__":
    main()
