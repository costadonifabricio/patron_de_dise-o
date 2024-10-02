### Ejercicio 1:

class Configuracion {
private static instancia: Configuracion;
private idioma: string = "";
private rutaBaseDatos: string = "";
private nivelRegistro: string = "";

private constructor() {}

public static getInstancia(): Configuracion {
if (!Configuracion.instancia) {
Configuracion.instancia = new Configuracion();
}
return Configuracion.instancia;
}

public obtenerIdioma(): string {
return this.idioma;
}
public obtenerRutaBaseDatos(): string {
return this.rutaBaseDatos;
}
public obtenerNivelRegistro(): string {
return this.nivelRegistro;
}

public actualizarIdioma(idioma: string): void {
this.idioma = idioma;
}

public actualizarRutaBaseDatos(rutaBaseDatos: string): void {
this.rutaBaseDatos = rutaBaseDatos;
}

public actualizarNivelRegistro(nivelRegistro: string): void {
this.nivelRegistro = nivelRegistro;
}
}

const configuracion = Configuracion.getInstancia();
configuracion.actualizarIdioma("Español");
configuracion.actualizarRutaBaseDatos("localhost");
configuracion.actualizarNivelRegistro("20");

console.log(configuracion.obtenerIdioma());
console.log(configuracion.obtenerRutaBaseDatos());
console.log(configuracion.obtenerNivelRegistro());

### Ejercicio 2:

class ConexionDB {
private static instancia: ConexionDB;
private host: string = "localhost";
private puerto: string = "3306";
private usuario: string = "root";

private constructor() {}

public static getInstancia(): ConexionDB {
if (!ConexionDB.instancia) {
ConexionDB.instancia = new ConexionDB();
}
return ConexionDB.instancia;
}

public conectar(): void {
console.log(
`Conectando a la base de datos en ${this.host}:${this.puerto} como ${this.usuario}...`
);
console.log("Conexión exitosa.");
}

public desconectar(): void {
console.log("Desconectando de la base de datos...");
console.log("Desconexión exitosa.");
}
}

const conexion1 = ConexionDB.getInstancia();
conexion1.conectar();

const conexion2 = ConexionDB.getInstancia();
conexion2.desconectar();

### Ejercicio 3:

interface DispositivoEntrada {
tipoConexion: string;
marca: string;
getDetalles(): string;
}

class Teclado implements DispositivoEntrada {
tipoConexion: string;
marca: string;

constructor(tipoConexion: string, marca: string) {
this.tipoConexion = tipoConexion;
this.marca = marca;
}

getDetalles(): string {
return `Teclado - Marca: ${this.marca}, Tipo de Conexión: ${this.tipoConexion}`;
}
}

class Ratón implements DispositivoEntrada {
tipoConexion: string;
marca: string;

constructor(tipoConexion: string, marca: string) {
this.tipoConexion = tipoConexion;
this.marca = marca;
}

getDetalles(): string {
return `Ratón - Marca: ${this.marca}, Tipo de Conexión: ${this.tipoConexion}`;
}
}

class Scanner implements DispositivoEntrada {
tipoConexion: string;
marca: string;

constructor(tipoConexion: string, marca: string) {
this.tipoConexion = tipoConexion;
this.marca = marca;
}

getDetalles(): string {
return `Scanner - Marca: ${this.marca}, Tipo de Conexión: ${this.tipoConexion}`;
}
}

class DispositivoEntradaFactory {
public static crearDispositivo(
tipo: string,
tipoConexion: string,
marca: string
): DispositivoEntrada {
switch (tipo.toLowerCase()) {
case "teclado":
return new Teclado(tipoConexion, marca);
case "ratón":
return new Ratón(tipoConexion, marca);
case "scanner":
return new Scanner(tipoConexion, marca);
default:
throw new Error("Tipo de dispositivo no encontrado");
}
}
}

const teclado = DispositivoEntradaFactory.crearDispositivo(
"Teclado",
"USB",
"Logitech"
);
const ratón = DispositivoEntradaFactory.crearDispositivo(
"Ratón",
"Bluetooth",
"HP"
);
const scanner = DispositivoEntradaFactory.crearDispositivo(
"Scanner",
"USB",
"Canon"
);

console.log(teclado.getDetalles());
console.log(ratón.getDetalles());
console.log(scanner.getDetalles());

### Ejercicio 4:

interface PerifericoSalida {
modelo: string;
getDetalles(): string;
}

class Monitor implements PerifericoSalida {
modelo: string;
resolucion: string;

constructor(modelo: string, resolucion: string) {
this.modelo = modelo;
this.resolucion = resolucion;
}

getDetalles(): string {
return `Monitor - Modelo: ${this.modelo}, Resolución: ${this.resolucion}`;
}
}

class Impresora implements PerifericoSalida {
modelo: string;
tipoImpresion: string;

constructor(modelo: string, tipoImpresion: string) {
this.modelo = modelo;
this.tipoImpresion = tipoImpresion;
}

getDetalles(): string {
return `Impresora - Modelo: ${this.modelo}, Tipo de Impresión: ${this.tipoImpresion}`;
}
}

class Proyector implements PerifericoSalida {
modelo: string;
brillo: string;

constructor(modelo: string, brillo: string) {
this.modelo = modelo;
this.brillo = brillo;
}

getDetalles(): string {
return `Proyector - Modelo: ${this.modelo}, Brillo: ${this.brillo}`;
}
}

class PerifericoSalidaFactory {
public static crearPeriferico(
tipo: string,
modelo: string,
atributo: string
): PerifericoSalida {
switch (tipo.toLowerCase()) {
case "monitor":
return new Monitor(modelo, atributo);
case "impresora":
return new Impresora(modelo, atributo);
case "proyector":
return new Proyector(modelo, atributo);
default:
throw new Error("Tipo de periférico no encontrado");
}
}
}

const monitor = PerifericoSalidaFactory.crearPeriferico(
"Monitor",
"Samsung",
"1920x1080"
);
const impresora = PerifericoSalidaFactory.crearPeriferico(
"Impresora",
"Epson",
"Inyección de tinta"
);
const proyector = PerifericoSalidaFactory.crearPeriferico(
"Proyector",
"Benq",
"3000 lumens"
);

console.log(monitor.getDetalles());
console.log(impresora.getDetalles());
console.log(proyector.getDetalles());

### Ejercicio 5:

interface Observador {
notificar(nombreEquipo: string): void;
}

class DepartamentoMantenimiento implements Observador {
notificar(nombreEquipo: string): void {
console.log(
`Notificación: ${nombreEquipo} necesita mantenimiento preventivo.`
);
}
}

class Equipo {
private observadores: Observador[] = [];
public tiempoUso: number = 0;
public nombre: string;
public tipo: string;
public estado: string;
private umbralUso: number;

constructor(nombre: string, tipo: string, estado: string, umbralUso: number) {
this.nombre = nombre;
this.tipo = tipo;
this.estado = estado;
this.umbralUso = umbralUso;
}

agregarObservador(observador: Observador): void {
this.observadores.push(observador);
}

usarEquipo(horas: number): void {
this.tiempoUso += horas;
console.log(
`${this.nombre} ha sido utilizado por ${horas} horas. Tiempo total: ${this.tiempoUso} horas.`
);
this.notificarSiNecesitaMantenimiento();
}

private notificarSiNecesitaMantenimiento(): void {
if (this.tiempoUso >= this.umbralUso) {
this.observadores.forEach((obs) => obs.notificar(this.nombre));
}
}
}

const equipo1 = new Equipo("Compresora", "Mantenimiento", "Operativo", 10);
const mantenimiento = new DepartamentoMantenimiento();

equipo1.agregarObservador(mantenimiento);
equipo1.usarEquipo(5);
equipo1.usarEquipo(6);

### Ejercicio 6:

interface ObservadorInventario {
actualizar(inventario: string[]): void;
}

class InterfazUsuario implements ObservadorInventario {
actualizar(inventario: string[]): void {
console.log(`Inventario actualizado: ${inventario.join(", ")}`);
}
}

class Inventario {
private equipos: string[] = [];
private observadores: ObservadorInventario[] = [];

agregarObservador(observador: ObservadorInventario): void {
this.observadores.push(observador);
}

agregarEquipo(nombreEquipo: string): void {
this.equipos.push(nombreEquipo);
console.log(`Equipo ${nombreEquipo} agregado al inventario.`);
this.notificarObservadores();
}

eliminarEquipo(nombreEquipo: string): void {
this.equipos = this.equipos.filter((equipo) => equipo !== nombreEquipo);
console.log(`Equipo ${nombreEquipo} eliminado del inventario.`);
this.notificarObservadores();
}

private notificarObservadores(): void {
this.observadores.forEach((obs) => obs.actualizar(this.equipos));
}
}

const inventario = new Inventario();
const interfaz1 = new InterfazUsuario();
const interfaz2 = new InterfazUsuario();

inventario.agregarObservador(interfaz1);
inventario.agregarObservador(interfaz2);

inventario.agregarEquipo("Compresora");
inventario.agregarEquipo("Generador");
inventario.eliminarEquipo("Compresora");

### Ejercicio 7:

interface IFacturacion {
generarFactura(cliente: string, monto: number): string;
consultarFactura(id: number): string;
}

class FacturacionVieja {
crearFactura(cliente: string, monto: number): string {
return `Factura creada para ${cliente} por un monto de $${monto}.`;
}

obtenerFactura(id: number): string {
return `Factura con ID ${id} recuperada.`;
}
}

class AdaptadorFacturacion implements IFacturacion {
private facturacionVieja: FacturacionVieja;

constructor(facturacionVieja: FacturacionVieja) {
this.facturacionVieja = facturacionVieja;
}

generarFactura(cliente: string, monto: number): string {
return this.facturacionVieja.crearFactura(cliente, monto);
}

consultarFactura(id: number): string {
return this.facturacionVieja.obtenerFactura(id);
}
}

const facturacionVieja = new FacturacionVieja();
const adaptadorFacturacion = new AdaptadorFacturacion(facturacionVieja);

console.log(adaptadorFacturacion.generarFactura("DuglasCosta", 150));
console.log(adaptadorFacturacion.consultarFactura(1));

### Ejercicio 8:

interface IProveedor {
obtenerProductos(): string[];
actualizarInventario(producto: string, cantidad: number): string;
}

class ProveedorExternoAPI {
fetchProductos(): string[] {
return ["Producto A", "Producto B", "Producto C"];
}

updateStock(producto: string, cantidad: number): string {
return `Stock de ${producto} actualizado a ${cantidad}.`;
}
}

class AdaptadorProveedor implements IProveedor {
private proveedorExterno: ProveedorExternoAPI;

constructor(proveedorExterno: ProveedorExternoAPI) {
this.proveedorExterno = proveedorExterno;
}

obtenerProductos(): string[] {
return this.proveedorExterno.fetchProductos();
}

actualizarInventario(producto: string, cantidad: number): string {
return this.proveedorExterno.updateStock(producto, cantidad);
}
}

const proveedorExterno = new ProveedorExternoAPI();
const adaptadorProveedor = new AdaptadorProveedor(proveedorExterno);

console.log(adaptadorProveedor.obtenerProductos());
console.log(adaptadorProveedor.actualizarInventario("Producto A", 50));
