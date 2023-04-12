# Introspector

Este es un migrador de bases de datos que utiliza [drizzle-kit](https://github.com/drizzle-team/drizzle-kit-mirror) para realizar introspecciones de una base de datos y generar una directorio con los siguientes archivos:  
  
📦 <root del proyecto>  
 └ 📂 (nombre seleccionado para el directorio en -out= *info más adelante)  
    └ 📂 meta  
      ├ 📜 _journal.json  
      ├ 📜 0000_snapshot.json  
    └ 📜 0000_icy_stranger.sql  
    └ 📜 schema.ts  
  
- [tag].sql: con las queries necesarias para crear las tablas de la base de datos introspeccionada. Donde [tag] es un identificador único generado por la librería.  
- schema.ts: para realizar inferencias de tipado en proyectos de typescript, útil para proyectos de desarrollo en typescript.  
- /meta:  
└ _journal.json: un diario con la version de la base de datos con información como ser timestamps y tags de cada migración.  
└ [id]_snapshot.json: una snapshot de las tablas de la base de datos al realizar la mgiacion en formato .json.  

  
Para hacer uso de este repositorio en tu máquina local se necesita:  
- (Node.js)[https://nodejs.org/es]  
y recomiendo (git)[https://git-scm.com/]  

Teniendo eso puedes ir a un directorio, abrir tu terminal y ejecutar los siguientes comandos:  

```
git clone https://github.com/gabrieladrianmezar/drizzle-kit-introspector.git 
cd migrador
npm i
```  

Eso sería el setup, ya estás listo para empezar a introspeccionar bases de datos con:  

```
npx drizzle-kit introspect:mysql --out= --host= --port= --user= --password= --database=
```
  
Ejemplo:  
```
npx drizzle-kit introspect:mysql --out=app-web/ --host=127.0.0.1 --port=3360 --user=root --password=root --database=app-web
```

Al ejecutar ese comando, drizzle-kit comenzará a instrospeccionar la base de datos y generar el directorio con los archivos comentados anteriormente.
