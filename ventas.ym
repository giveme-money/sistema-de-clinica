ventas = {}
contador_episodios = 1

def crear_episodio():
    global contador_episodios
    paciente = input("codigo paciente: ")
    fecha = input("fecha (aaaa-mm-dd): ")
    ventas[contador_episodios] = {
        "paciente": paciente,
        "fecha": fecha,
        "items": [],
        "costo": 0,
        "venta": 0
    }
    print("episodio", contador_episodios, "creado")
    contador_episodios += 1

def registrar_atencion():
    id_ep = int(input("numero de episodio: "))
    if id_ep not in ventas:
        print("episodio no existe")
        return
    tipo = input("tipo (productos, farmacos, insumos, prestaciones): ")
    codigo = input("codigo item: ")
    cantidad = int(input("cantidad: "))
    costo_unitario = float(input("costo unitario: "))
    margen = {"productos":0.6,"farmacos":0.5,"insumos":0.4,"prestaciones":0.55}
    if tipo not in margen:
        print("tipo no valido")
        return
    costo_total = cantidad * costo_unitario
    precio_venta = costo_total * (1 + margen[tipo])
    ventas[id_ep]["items"].append((tipo, codigo, cantidad, costo_unitario))
    ventas[id_ep]["costo"] += costo_total
    ventas[id_ep]["venta"] += precio_venta
    print("atencion registrada")

def calcular_precio():
    id_ep = int(input("numero de episodio: "))
    if id_ep not in ventas:
        print("episodio no existe")
        return
    datos = ventas[id_ep]
    margen = datos["venta"] - datos["costo"]
    print("costo:", datos["costo"])
    print("venta:", datos["venta"])
    print("margen:", margen)

def reporte_ventas():
    desde = input("desde (aaaa-mm-dd): ")
    hasta = input("hasta (aaaa-mm-dd): ")
    print("reporte de ventas:")
    for id_ep, datos in ventas.items():
        if desde <= datos["fecha"] <= hasta:
            margen = datos["venta"] - datos["costo"]
            print("episodio", id_ep, "- paciente:", datos["paciente"], 
                  "- costo:", datos["costo"], 
                  "- venta:", datos["venta"], 
                  "- margen:", margen)

def menu_ventas():
    while True:
        print("\nmenu ventas")
        print("1. crear episodio")
        print("2. registrar atencion")
        print("3. calcular precio")
        print("4. reporte de ventas")
        print("5. volver")
        opcion = input("elige una opcion: ")
        if opcion == "1":
            crear_episodio()
        elif opcion == "2":
            registrar_atencion()
        elif opcion == "3":
            calcular_precio()
        elif opcion == "4":
            reporte_ventas()
        elif opcion == "5":
            break
        else:
            print("opcion no valida")

def main():
    while True:
        print("\nsistema de salud")
        print("1. maestros")
        print("2. inventario")
        print("3. produccion")
        print("4. ventas")
        print("5. salir")
        opcion = input("elige una opcion: ")
        if opcion == "1":
            menu_maestros()
        elif opcion == "2":
            menu_inventario()
        elif opcion == "3":
            menu_produccion()
        elif opcion == "4":
            menu_ventas()
        elif opcion == "5":
            print("saliendo...")
            break
        else:
            print("opcion no valida")

if __name__ == "__main__":
    main()
