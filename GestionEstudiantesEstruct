#include <iostream>
#include <vector>
#include <string>
#include <iomanip>
#include <fstream>   // Para manejo de archivos
#include <sstream>   // Para procesar líneas de texto

using namespace std;

struct Estudiante {
    int id;
    string nombre;
    string curso;
    float promedio;
    int edad;  // Nuevo campo para la edad

    Estudiante(int id, string nombre, string curso, float promedio, int edad)
        : id(id), nombre(nombre), curso(curso), promedio(promedio), edad(edad) {}
};

class SistemaGestionEstudiantes {
private:
    vector<Estudiante> estudiantes;

public:
    void agregarEstudiante() {
        int id, edad;
        string nombre, curso;
        float promedio;

        cout << "Ingrese el ID del estudiante: ";
        cin >> id;
        cin.ignore();
        cout << "Ingrese el nombre del estudiante: ";
        getline(cin, nombre);
        cout << "Ingrese el curso del estudiante: ";
        getline(cin, curso);
        cout << "Ingrese el promedio del estudiante: ";
        cin >> promedio;
        cout << "Ingrese la edad del estudiante: ";  // Solicitar edad
        cin >> edad;

        estudiantes.push_back(Estudiante(id, nombre, curso, promedio, edad));
        cout << "Estudiante agregado exitosamente." << endl;
    }

    void mostrarEstudiantes() {
        if (estudiantes.empty()) {
            cout << "No hay estudiantes registrados." << endl;
            return;
        }
        cout << "Lista de estudiantes:\n";
        cout << left << setw(10) << "ID" << setw(20) << "Nombre" << setw(20) << "Curso" 
             << setw(10) << "Edad" << "Promedio\n";
        cout << "---------------------------------------------------------------\n";
        for (const auto& estudiante : estudiantes) {
            cout << setw(10) << estudiante.id << setw(20) << estudiante.nombre
                 << setw(20) << estudiante.curso << setw(10) << estudiante.edad
                 << estudiante.promedio << endl;
        }
    }

    void editarEstudiante() {
        int id;
        cout << "Ingrese el ID del estudiante a editar: ";
        cin >> id;
        bool encontrado = false;

        for (auto& estudiante : estudiantes) {
            if (estudiante.id == id) {
                encontrado = true;
                cout << "Estudiante encontrado. Ingrese los nuevos datos.\n";
                cin.ignore();
                cout << "Nuevo nombre: ";
                getline(cin, estudiante.nombre);
                cout << "Nuevo curso: ";
                getline(cin, estudiante.curso);
                cout << "Nuevo promedio: ";
                cin >> estudiante.promedio;
                cout << "Nueva edad: ";
                cin >> estudiante.edad;
                cout << "Datos del estudiante actualizados exitosamente." << endl;
                break;
            }
        }

        if (!encontrado) {
            cout << "Estudiante con ID " << id << " no encontrado.\n";
        }
    }

    void mostrarPromedioNotas() {
        if (estudiantes.empty()) {
            cout << "No hay estudiantes registrados.\n";
            return;
        }

        float sumaPromedios = 0;
        for (const auto& estudiante : estudiantes) {
            sumaPromedios += estudiante.promedio;
        }

        float promedioGeneral = sumaPromedios / estudiantes.size();
        cout << "El promedio de las notas de todos los estudiantes es: " << promedioGeneral << endl;
    }

    void guardarDatos(const string& nombreArchivo) {
        ofstream archivo(nombreArchivo);
        if (!archivo) {
            cout << "No se pudo abrir el archivo para guardar los datos." << endl;
            return;
        }
        for (const auto& estudiante : estudiantes) {
            archivo << estudiante.id << "," << estudiante.nombre << "," 
                    << estudiante.curso << "," << estudiante.promedio << "," 
                    << estudiante.edad << "\n";  // Guardamos también la edad
        }
        archivo.close();
        cout << "Datos guardados en " << nombreArchivo << endl;
    }

    void cargarDatos(const string& nombreArchivo) {
        ifstream archivo(nombreArchivo);
        if (!archivo) {
            cout << "No se pudo abrir el archivo para cargar los datos." << endl;
            return;
        }

        estudiantes.clear();
        string linea;
        while (getline(archivo, linea)) {
            stringstream ss(linea);
            string idStr, nombre, curso, promedioStr, edadStr;

            if (getline(ss, idStr, ',') && getline(ss, nombre, ',') &&
                getline(ss, curso, ',') && getline(ss, promedioStr, ',') &&
                getline(ss, edadStr, ',')) {
                
                int id = stoi(idStr);
                float promedio = stof(promedioStr);
                int edad = stoi(edadStr);

                estudiantes.push_back(Estudiante(id, nombre, curso, promedio, edad));
            }
        }
        archivo.close();
        cout << "Datos cargados desde " << nombreArchivo << endl;
    }
};

int main() {
    SistemaGestionEstudiantes sistema;
    int opcion;

    // Cargar datos al inicio
    sistema.cargarDatos("estudiantes.txt");

    do {
        cout << "\nSistema de Gestion de Estudiantes\n";
        cout << "1. Agregar estudiante\n";
        cout << "2. Mostrar estudiantes\n";
        cout << "3. Editar estudiante\n";  // Opción de editar estudiante
        cout << "4. Mostrar promedio de notas\n";  // Opción de mostrar promedio
        cout << "5. Guardar datos en archivo\n";
        cout << "6. Salir\n";
        cout << "Elija una opcion: ";
        cin >> opcion;

        switch (opcion) {
            case 1:
                sistema.agregarEstudiante();
                break;
            case 2:
                sistema.mostrarEstudiantes();
                break;
            case 3:
                sistema.editarEstudiante();
                break;
            case 4:
                sistema.mostrarPromedioNotas();
                break;
            case 5:
                sistema.guardarDatos("estudiantes.txt");
                break;
            case 6:
                cout << "Saliendo del sistema...\n";
                break;
            default:
                cout << "Opción inválida, intente de nuevo.\n";
        }
    } while (opcion != 6);

    return 0;
}
