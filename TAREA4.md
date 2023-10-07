# C++
# ejercicio 1

#include <iostream>

using namespace std;

int calcularSubsidio(int hijos, int edad_escolar, bool viuda) {
    int subsidio_base = 0;

    // Determinar el subsidio base según la cantidad de hijos
    if (hijos <= 2) {
        subsidio_base = 70;
    } else if (hijos <= 5) {
        subsidio_base = 90;
    } else {
        subsidio_base = 120;
    }

    // Calcular el subsidio adicional por hijos en edad escolar
    int subsidio_edad_escolar = 0;
    if (edad_escolar >= 6 && edad_escolar <= 18) {
        subsidio_edad_escolar = 10 * (edad_escolar - 5);
    }

    // Calcular el subsidio adicional por viuda
    int subsidio_viuda = viuda ? 20 : 0;

    // Calcular el subsidio total
    int subsidio_total = subsidio_base + subsidio_edad_escolar + subsidio_viuda;

    return subsidio_total;
}

int main() {
    int hijos, edad_escolar;
    char viuda;

    cout << "Cantidad de hijos: ";
    cin >> hijos;
    cout << "Edad del hijo en edad escolar: ";
    cin >> edad_escolar;
    cout << "¿Es viuda la madre? (S/N): ";
    cin >> viuda;

    int monto_subsidio = calcularSubsidio(hijos, edad_escolar, viuda == 'S' || viuda == 's');

    cout << "La familia recibirá un subsidio de Q." << monto_subsidio << " mensuales." << endl;

    return 0;
}

# Pythom 
def calcularSubsidio(hijos, edad_escolar, viuda):
    subsidio_base = 0
    
    # Determinar el subsidio base según la cantidad de hijos
    if hijos <= 2:
        subsidio_base = 70
    elif hijos <= 5:
        subsidio_base = 90
    else:
        subsidio_base = 120
    
    # Calcular el subsidio adicional por hijos en edad escolar
    subsidio_edad_escolar = 0
    if 6 <= edad_escolar <= 18:
        subsidio_edad_escolar = 10 * (edad_escolar - 5)
    
    # Calcular el subsidio adicional por viuda
    subsidio_viuda = 20 if viuda else 0
    
    # Calcular el subsidio total
    subsidio_total = subsidio_base + subsidio_edad_escolar + subsidio_viuda
    
    return subsidio_total

# Ejemplo de uso:
hijos = int(input("Cantidad de hijos: "))
edad_escolar = int(input("Edad del hijo en edad escolar: "))
viuda = input("¿Es viuda la madre? (S/N): ").upper() == "S"

monto_subsidio = calcularSubsidio(hijos, edad_escolar, viuda)
print(f"La familia recibirá un subsidio de Q.{monto_subsidio} mensuales.")

# ejercicio 2
# c++ ejercicio 2

#include <iostream>
#include <vector>
#include <cstdlib>
#include <ctime>

using namespace std;

vector<int> llenarVectorAleatorio(int longitud) {
    vector<int> vector_aleatorio;
    for (int i = 0; i < longitud; i++) {
        vector_aleatorio.push_back(rand() % 100 + 1); // Llena el vector con números aleatorios entre 1 y 100
    }
    return vector_aleatorio;
}

string verificarEscenario(const vector<int>& vector_a, const vector<int>& vector_b) {
    int suma_a = 0;
    int suma_b = 0;
    for (int num : vector_a) {
        suma_a += num;
    }
    for (int num : vector_b) {
        suma_b += num;
    }

    if (suma_a == suma_b) {
        return "Los vectores son iguales.";
    } else if (suma_a < suma_b) {
        return "El vector A es menor que el vector B.";
    } else {
        return "El vector B es menor que el vector A.";
    }
}

int main() {
    srand(time(0)); // Inicializar la semilla para números aleatorios

    int longitud;
    cout << "Ingrese la longitud de los vectores: ";
    cin >> longitud;

    vector<int> vector_a = llenarVectorAleatorio(longitud);
    vector<int> vector_b = llenarVectorAleatorio(longitud);

    cout << "Vector A: ";
    for (int num : vector_a) {
        cout << num << " ";
    }
    cout << endl;

    cout << "Vector B: ";
    for (int num : vector_b) {
        cout << num << " ";
    }
    cout << endl;

    string resultado = verificarEscenario(vector_a, vector_b);
    cout << resultado << endl;

    return 0;
}

# pythom ejercicio 2

import random

def llenar_vector_aleatorio(longitud):
    return [random.randint(1, 100) for _ in range(longitud)]

def verificar_escenario(vector_a, vector_b):
    suma_a = sum(vector_a)
    suma_b = sum(vector_b)

    if suma_a == suma_b:
        return "Los vectores son iguales."
    elif suma_a < suma_b:
        return "El vector A es menor que el vector B."
    else:
        return "El vector B es menor que el vector A."

longitud = int(input("Ingrese la longitud de los vectores: "))
vector_a = llenar_vector_aleatorio(longitud)
vector_b = llenar_vector_aleatorio(longitud)

print("Vector A:", vector_a)
print("Vector B:", vector_b)

resultado = verificar_escenario(vector_a, vector_b)
print(resultado)

# ejercicio 3
# c++ ejercicio 3

#include <iostream>
#include <vector>
#include <limits>

using namespace std;

double calcularRango(const vector<double>& datos) {
    if (datos.empty()) {
        return 0.0;  // Si no hay datos, el rango es 0
    }

    double maximo = numeric_limits<double>::min();
    double minimo = numeric_limits<double>::max();

    for (double dato : datos) {
        if (dato > maximo) {
            maximo = dato;
        }
        if (dato < minimo) {
            minimo = dato;
        }
    }

    double rango = maximo - minimo;
    return rango;
}

int main() {
    int n;
    cout << "Ingrese la cantidad de datos: ";
    cin >> n;

    vector<double> datos;
    for (int i = 0; i < n; i++) {
        double dato;
        cout << "Ingrese el dato " << i + 1 << ": ";
        cin >> dato;
        datos.push_back(dato);
    }

    double rango_resultante = calcularRango(datos);
    cout << "El rango de los datos es: " << rango_resultante << endl;

    return 0;
}

# pythom ejercicio 3 
def calcularRango(datos):
    if len(datos) == 0:
        return 0  # Si no hay datos, el rango es 0

    maximo = max(datos)
    minimo = min(datos)
    rango = maximo - minimo
    return rango

# Solicitar al usuario la cantidad de datos
n = int(input("Ingrese la cantidad de datos: "))

# Solicitar al usuario ingresar los datos uno por uno
datos = []
for i in range(n):
    dato = float(input(f"Ingrese el dato {i + 1}: "))
    datos.append(dato)

# Calcular y mostrar el rango de los datos
rango_resultante = calcularRango(datos)
print(f"El rango de los datos es: {rango_resultante}")

# ejercicio 4 
# c++ ejercicio 4
#include <iostream>

using namespace std;

void dibujarCuadrado(int lado) {
    if (lado <= 0) {
        cout << "El lado del cuadrado debe ser mayor que cero." << endl;
        return;
    }

    for (int i = 0; i < lado; i++) {
        if (i == 0 || i == lado - 1) {
            for (int j = 0; j < lado; j++) {
                cout << "* ";
            }
        } else {
            cout << "* ";
            for (int j = 0; j < lado - 2; j++) {
                cout << "  ";
            }
            cout << "*";
        }
        cout << endl;
    }
}

int main() {
    int lado;
    cout << "Ingrese el lado del cuadrado: ";
    cin >> lado;

    dibujarCuadrado(lado);

    return 0;
}

# pythom ejercicio  4

def dibujarCuadrado(lado):
    if lado <= 0:
        print("El lado del cuadrado debe ser mayor que cero.")
        return

    for i in range(lado):
        if i == 0 or i == lado - 1:
            print("* " * lado)
        else:
            print("* " + "  " * (lado - 2) + "*")


lado = int(input("Ingrese el lado del cuadrado: "))


dibujarCuadrado(lado)



