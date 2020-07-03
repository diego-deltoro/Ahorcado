# Ahorcado
proyecto de la materia de programación, un ahorcado en c++

#include <iostream>
#include <string>
#include <ctime>
#include <cstdlib>
#include<fstream>
#include <string.h>
#include <cstdio>


using namespace std;

string palabra_original;
string palabra_mostrar;
string palara_ingresada;
int vidas;
clock_t a;
clock_t b;
float s;
int g;//opcion elegida
char n[5];
int vt = 10; 
float pa = 0; 


void mostrar();//funciones
void ingresar(char x);
int iniciar();
void caso1();
void caso2();
void agregar();
float wh();
void lectura();
float juego();
int uno();
int dos();
void getString(char* str);



int main(int argc, char* argv[])//main en donde se encuentra la union de las funciones
{

    lectura();



    juego();


    getString(n);

    cout << "\nescriba su nombre" << endl;
    cin >> n[0] >> n[1] >> n[2] >> n[3] >> n[4];

    agregar();


}

float juego() {
    int t;

    while (vt > 0) {
        iniciar();
        mostrar();
        uno();
        wh();
        if (vt > 0 && g == 1) {
            cout << "elige la  opcion 1" << endl;
            pa += 1;
        }
        if (vt > 0 && g == 2) {
            cout << "elige la  opcion 2 y escriba una nueva palabra" << endl;
            pa += 1;
        }

        palabra_mostrar = "";
        palabra_original = "";

    }



    dos();
    t = b - a;
    s = float(t) / CLOCKS_PER_SEC;



    if (vidas > 0) {//si vidas es mayor a 0 y son iguales las palabras, ganas
        cout << "  GANO" << endl;

        cout << "durante " << s << " segundos";

    }


    else {//si no, se imprime el ahorcado entero y perdiste
        cout << "\n\tperdio " << endl;
        cout << "___________\n         ||\n         ||\n        _||_\n       /    \\\n       \\    /\n        _||_\n       /    \\\n      // || \\\\\n     //  ||  \\\\\n         ||\n        _||_\n       /    \\\n      //    \\\\\n     //      \\\\" << endl;
    }
    return s,pa;
}

float wh() {
    while (vidas > 0 && palabra_mostrar != palabra_original) {//mientras que vidas sea mayor a 0 y la palabra original no sea igual a la mostrada(con guiones)
        char x;
        cin >> x;//ingresa un carcater
        system("cls"); //limpiar el monitor para mas claridad
        ingresar(x);
        mostrar();

    }

    return vidas, vt;
}

void getString(char* str) {
    strcpy_s(str, 5, "test");

}


void mostrar() {//en esta función se imprime a pantalla las vidas y el avance correspondiente del ahorcado
    cout << "   vidas: " << vidas << endl;//imprimir numero de vidas
    cout << "   vt: " << vt << endl;
    cout << "   " << palabra_mostrar << endl;//imprimir las letras acertadas 
    if (vidas == 5) {//condicional para imprimir una imagen específica del ahorcado dependiento del avance 
        cout << "___________\n         ||\n         ||" << endl;


    }
    else if (vidas == 4) {
        cout << "___________\n         ||\n         ||\n        _||_\n       /    \\\n       \\    /" << endl;


    }
    else if (vidas == 3) {
        cout << "___________\n         ||\n         ||\n        _||_\n       /    \\\n       \\    /\n        _|\n       /   \n      //    \n     //     " << endl;

    }
    else if (vidas == 2) {
        cout << "___________\n         ||\n         ||\n        _||_\n       /    \\\n       \\    /\n        _||_\n       /    \\\n      //    \\\\\n     //      \\\\" << endl;

    }
    else if (vidas == 1) {//figura del ahorcado
        cout << "___________\n         ||\n         ||\n        _||_\n       /    \\\n       \\    /\n        _||_\n       /    \\\n      // || \\\\\n     //  ||  \\\\\n         ||" << endl;

    }

}

int iniciar() {//
    vidas = 5;//empieza con 5 vidas pero puede cambiarse aqui 



    cout << "\n\t1: si quiere jugar contra CPU" << endl;
    cout << "\t2: si desea ingresar una palabra (en minusuclas)" << endl;
    cout << "   ";
    cin >> g;//se elige una opcion 


    if (g == 2) {//condicional para opcion de ingresar una palabra en caso de ser más de 2 jugadores
        caso2();
    }
    else if (g == 1) {//en caso de jugar contra cpu 
        caso1();
    }



    for (int i = 0; i < palabra_original.length(); i++) {//el i va de 0 hasta la longitud de la palabra, aumenta de uno
        if (palabra_original[i] >= 'a' && palabra_original[i] <= 'z') {
            palabra_mostrar += '-';//a cada caracter se le agrega un guión
        }
        else {
            palabra_mostrar += palabra_original[i];//si no es una letra minuscula, se deja igual
        }
    }
    return g; 
}

void caso2() {
    cout << "\tingrese una palabra" << endl;

    cin >> palara_ingresada;
    palabra_original = palara_ingresada;//se define la palabra original igualando a la palabra ingresada

}



void caso1() {
    int w;//numero de palabra elegida
    string palabras_definidas[15] = { "avion","television","fisico","helicoptero","cohete","cielo","arbol","computadora","programador","doctor","serie","presidente","policia","cuchara","gorra" };
    //el string y arreglo para separar los 15 espacios de cadena de caracteres y se define a un lado cada una, igual se pueden modificar
    cout << "\tEscriba un número entre 1 y 15 para elegir una palabra" << endl;
    cout << "   ";
    cin >> w; {//eleccion de palabra entre las 15 disponibles
        switch (w) {//en cada caso se iguala la palabra original a una de las del espacio reservado en el arreglo de palabras definidas
        case 1: palabra_original = palabras_definidas[0];
            break;
        case 2: palabra_original = palabras_definidas[1];
            break;
        case 3: palabra_original = palabras_definidas[2];
            break;
        case 4: palabra_original = palabras_definidas[3];
            break;
        case 5: palabra_original = palabras_definidas[4];
            break;
        case 6: palabra_original = palabras_definidas[5];
            break;
        case 7: palabra_original = palabras_definidas[6];
            break;
        case 8: palabra_original = palabras_definidas[7];
            break;
        case 9: palabra_original = palabras_definidas[8];
            break;
        case 10: palabra_original = palabras_definidas[9];
            break;
        case 11: palabra_original = palabras_definidas[10];
            break;
        case 12: palabra_original = palabras_definidas[11];
            break;
        case 13: palabra_original = palabras_definidas[12];
            break;
        case 14: palabra_original = palabras_definidas[13];
            break;
        case 15: palabra_original = palabras_definidas[14];
            break;
        default:
            cout << "   elija un número correcto";
            break;
        }
    }
}
void ingresar(char x) {
    bool perdiVidas = true;

    for (int i = 0; i < palabra_original.length(); i++) {//revisa cada letrea
        if (x == palabra_original[i]) {//si el caracter es igual a alguno de la palabra
            perdiVidas = false;//no pierdes vidas
            palabra_mostrar[i] = x;//y se sustituye el caracter por el guion
        }
    }
    if (perdiVidas) {
        vidas = vidas - 1;//si no, pierdes una vida
        vt -= 1;

    }
}



void lectura() {
    ifstream historial;
    string texto;


    historial.open("historial.txt", ios::in); //Abrimos el archivo en modo lectura

    if (historial.fail()) {
        cout << "No se pudo abrir el archivo";
        exit(1);
    }

    while (!historial.eof()) { //mientras no sea final del archivo
        getline(historial, texto);
        cout << "\n" << texto << endl;
    }

    historial.close(); //Cerramos el archivo
}

void agregar() {
    ofstream historial;
    float x;
    x = s;
    historial.open("historial.txt", ios::app); //abirmeos el texto en modo aregar
    if (historial.fail()) {
        cout << "No se pudo abrir el archivo";
        exit(1);
    }

    if (vt <= 0) {
        historial << "\n" << n << " ----- " << x << " s" << " ---- " << pa << " acertadas";
    }
  


    historial.close();//cerramos
}

int uno() {
    a = clock();
    return a;
}

int dos() {
    b = clock();
    return b;
}
