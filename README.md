[9:51 p. m., 16/5/2022] 𝘭𝘪𝘻 ღ: #include <iostream>
#include <conio.h>
#include <string.h>
#include <string>
#include <fstream>
#include<stdlib.h>// funcione new y delete
#include <vector>

using namespace std;

//definir la funcion
void Alta();
void modificar();
void eliminar();
void listas();
void archivos();


int alta, * hora,* minu, * preciounitt, * cantt, * preciounit, * total, * subtotal, * iva, * numcita;
string * nombre, * nombtrat, * desc;
int main()
{
	int opc;
	cout << "BIENVENIDO AL MENU DE OPCIONES" << endl;
	cout << "Ingrese una de las siguientes opciones" << endl;
	cout << "1.-Alta de registros" << endl << "2.-Modificar cita" << endl << "3.-Eliminar cita" << endl << "4.-Lista de registros" << endl << "5.-Limpiar pantalla" << endl << "6.-Salir" << endl;
	cin >> opc;

	switch…
[10:53 p. m., 16/5/2022] 𝘭𝘪𝘻 ღ: #include <iostream>
#include <conio.h>
#include <string.h>
#include <string>
#include <fstream>
#include<stdlib.h>// funcione new y delete
#include <vector>

using namespace std;

//definir la funcion
void Alta();
void modificar();
void eliminar();
void listas();
void archivos();


int alta, * hora,* minu, * cantt, * preciounit, * total, * subtotal, * iva, * numcita;
string* nombre, * nombtrat, * descrip;
int main()
{
	int opc;
	cout << "BIENVENIDO AL MENU DE OPCIONES" << endl;
	cout << "Ingrese una de las siguientes opciones" << endl;
	cout << "1.-Alta de registros" << endl << "2.-Modificar cita" << endl << "3.-Eliminar cita" << endl << "4.-Lista de registros" << endl << "5.-Limpiar pantalla" << endl << "6.-Salir" << endl;
	cin >> opc;

	switch (opc)
	{
	case 1:
		Alta();
		return main();
		break;

	case 2:
		modificar();
		return main();
		break;

	case 3:
		eliminar();
		return main();
		break;

	case 4:
		listas();
		return main();
		break;

	case 5:
		system("cls"); //system("clear");
		return main();
		break;

	case 6:
		archivos();
		break;
	}
}

void Alta()
{
	cout << "Digite el num de registros que desea dar de alta" << endl;
	cin >> alta;
	nombre = new string[alta];
	hora = new int[alta];
	minu = new int[alta];
	nombtrat = new string[alta];
	descrip = new string[alta];
	cantt = new int[alta];
	preciounit = new int[alta];
	subtotal = new int[alta];
	iva = new int[alta];
	total = new int[alta];

	for (int i = 0; i < alta; i++)
	{

		cout << "Numero de cita" << i + 1 << endl;
		while (getchar() != '\n');
		cout << "Ingrese nombre" << endl;
		getline(cin, nombre[i]); //espacios
		cout << "Ingrese hora" << endl;
		cin >> hora[i] >> minu[i];
		while (getchar() != '\n');
		cout << "Nombre del tratamiento" << endl;
		getline(cin, nombtrat[i]); //espacios
		while (getchar() != '\n');
		cout << "Descripcion" << endl;
		getline(cin, descrip[i]); //espacios
		cout << "Cantidad" << endl;
		cin >> cantt[i];
		cout << "Precio unitario" << endl;
		cin >> preciounit[i];
		cout << "Subtotal" << endl;
		subtotal[i] = (preciounit[i] * cantt[i]);
		cout << subtotal[i] << endl;
		cout << "IVA" << endl;
		iva[i] = (16 * subtotal[i] / 100);
		cout << iva[i] << endl;
		cout << "El total es" << endl;
		total[i] = (subtotal[i] + iva[i]);
		cout << total[i] << endl;
	}
}

void modificar()
{
	int j, opcion;
	cout << "ingrese el numero registro a modificar";
	cin >> j;
	j = j - 1; // esto debido a que i inicia en 0
	cout << "Ingrese la opcion a modificar" << endl;
	cout << "1. - Nombre del paciente" << endl;
	cout << "2. - Hora de cita" << endl;
	cin >> opcion;

	switch (opcion)
	{
	case 1:
		for (int i = j; i == j; i++)
		{
			while (getchar() != '\n'); //se vacia el buffer o el espacio
			cout << "Ingrese nombre del paciente" << endl;
			getline(cin, nombre[i]);
		}
		break;

	case 2:
		for (int i = j; i == j; i++)
		{
			cout << "Ingrese hora" << endl;
			cin >> hora[i];
			cin >> minu[i];
		}
	}


}

void eliminar()
{
	int j;
	cout << "ingrese el  registro a eliminar";
	cin >> j;
	j = j - 1;
	for (int i = j; i == j; i++)
	{
		cout << "Eliminando registro" << j + 1 << endl;

		nombre[i] = " ";
		hora[i] = 0;
		minu[i] = 0;
		nombtrat[i] = " ";
		descrip[i] = " ";
		cantt[i] = 0;
		preciounit[i] = 0;
		subtotal[i] = 0;
		iva[i] = 0;
		total[i] = 0;
	}
}

void listas()
{
	for (int i = 0; i < alta; i++)
	{
		if (nombre[i] == " ")
		{
			cout << "REGISTRO ELIMINADO" << i + 1 << endl;
		}
		else
		{
			cout << " registro" << i + 1 << endl;
			cout << nombre[i] << endl;
			cout << hora[i] << endl;
			cout << minu[i] << endl;
			cout << nombtrat[i] << endl;
			cout << descrip[i] << endl;
			cout << cantt[i] << endl;
			cout << preciounit[i] << endl;
			cout << subtotal[i] << endl;
			cout << iva[i] << endl;
			cout << total[i] << endl;
		}
	}
}

void archivos()
{
	int numcita;
	ofstream archivo; //clase ifstream para leer archivos
	string nombrearchivo;
	int texto;
	string texto2;

	nombrearchivo = "altaregistros";

	archivo.open(nombrearchivo.c_str(), ios::out);

	if (archivo.fail())
	{
		cout << "ERROR NO SE PUDO CREAR EL ARCHIVO";
		exit(1);
	}

	archivo << "NUMERO DE CITA" << "\t";
	archivo << "NOMBRE" << "\t";
	archivo << "HORA" << "\t";
	archivo << "MINUTOS" << "\t";
	archivo << "NOMBRE DEL TRATAMIENTO" << "\t";
	archivo << "DESCRIPCION" << "\t";
	archivo << "PRECIO UNITARIO DEL TRATAMIENTO" << "\n";
	archivo << "CANTIDAD TRATAMIENTO" << "\t";
	archivo << "PRECIO UNITARIO" << "\t";
	archivo << "SUBTOTAL" << "\t";
	archivo << "IVA" << "\t";
	archivo << "TOTAL" << "\t";

	for (int i = 0; i < alta; i++)
	{
		if (nombre[i] == " ")
		{

		}
		else
		{
			texto2 = nombre[i];
			archivo << texto2 << "\t" << "\t";
			texto = hora[i];
			archivo << texto << "\t " << "\t";
			texto = minu[i];
			archivo << texto << "\t " << "\t";
			texto2 = nombtrat[i];
			archivo << texto2 << "\t " << "\t";
			texto2 = descrip[i];
			archivo << texto2 << "\t " << "\t";
			texto = cantt[i];
			archivo << texto << "\t" << "\t";
			texto = preciounit[i];
			archivo << texto << "\t" << "\t";
			texto = subtotal[i];
			archivo << texto << "\t" << "\t";
			subtotal[i] = (preciounit[i] * cantt[i]);
			texto = subtotal[i];
			texto = iva[i];
			archivo << texto << "\t" << "\t";
			iva[i] = (16 * subtotal[i] / 100);
			texto = iva[i];
			texto = total[i];
			archivo << texto << "\t" << "\t";
			total[i] = (subtotal[i] + iva[i]);
			texto = total[i];
		}
	}

	archivo.close();
}
