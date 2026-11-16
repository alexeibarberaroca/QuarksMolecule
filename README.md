<h1 align="center">QuarksMolecule 🧪</h1>

<p align="center"><strong>Calcula las propiedades físicas y químicas de una molécula, hasta la masa de sus quarks, con PL/SQL sobre Oracle.</strong></p>

<p align="center">
  <img alt="PL/SQL" src="https://img.shields.io/badge/PL%2FSQL-Oracle-f80000">
  <img alt="Base de datos Oracle" src="https://img.shields.io/badge/Oracle-Database-f80000">
  <img alt="Licencia GPL v3" src="https://img.shields.io/badge/licencia-GPLv3-22c55e">
</p>

---

Escribe la fórmula de una molécula (por ejemplo `H2O`) y su peso, y **QuarksMolecule** calcula cuántos moles, moléculas y átomos hay, cuántos protones y neutrones, y la masa de los quarks *up* y *down* que los componen, en varias unidades (MeV/c², eV/c², julios/c² y kilogramos).

Es un proyecto **íntegramente en PL/SQL**: toda la lógica vive en tablas, funciones y procedimientos de una base de datos **Oracle**. Nació como ejercicio para llevar la física de partículas al terreno de las bases de datos, durante mi formación en administración de sistemas.

> 🔬 **La versión moderna de esta idea** está integrada en **[AtomicWorld](https://relativedevelopers.com/atomicworld/)**, de Relative Developers, donde el cálculo es interactivo y en 3D. Este repositorio es la implementación original en base de datos.

---

## ✨ Qué calcula

A partir de una fórmula y un peso, para cada elemento de la molécula:

- **Masa atómica total** de la molécula y **número de moles**.
- **Número de moléculas** y de **átomos** de cada elemento.
- **Protones y neutrones** de cada elemento.
- **Quarks up y down** de esos protones y neutrones.
- **Conversión de masa** de los quarks: MeV/c² → eV/c² → J/c² → kg.

También incluye funciones para **bases nitrogenadas y aminoácidos** (ADN/ARN): nombre y fórmula química de cada una.

---

## 🧠 Cómo está organizado

```
PL_SQL/
├── Tables/          Elementos, partículas, subpartículas, bases nitrogenadas, aminoácidos...
├── Functions/       Peso atómico, moles, moléculas, átomos, protones, neutrones y quarks
├── Functions ARN/   Nombres y fórmulas de aminoácidos y bases nitrogenadas
├── Procedures/      Los procedimientos principales + ejemplos de uso
├── ALL_TABLES.sql   Crea todas las tablas de golpe
├── ALL_FUNCTIONS.sql Crea todas las funciones de golpe
└── DROP_TABLES.sql  Elimina las tablas
```

Los datos no están inventados: las masas de los quarks, los electrones y demás subpartículas, y las masas atómicas de los elementos, están cargados como datos reales del Modelo Estándar y de la tabla periódica.

---

## 🚀 Puesta en marcha

Necesitas una base de datos **Oracle** (por ejemplo Oracle XE) y un cliente como SQL\*Plus, SQL Developer o VS Code con la extensión de Oracle.

Ejecuta los scripts **en este orden**:

```sql
@PL_SQL/ALL_TABLES.sql       -- 1. Crea las tablas y carga los datos
@PL_SQL/ALL_FUNCTIONS.sql    -- 2. Crea las funciones
@PL_SQL/Procedures/Subparticles_ChemicalFormulas.sql     -- 3. Crea el procedimiento
```

---

## 🎮 Cómo se usa

Activa la salida por pantalla y llama al procedimiento con el **peso** y la **fórmula**:

```sql
SET SERVEROUTPUT ON;

CALL Subparticles_ChemicalFormulas(1, 'H2O');
CALL Subparticles_ChemicalFormulas(1, 'C5H5N5O1');
CALL Subparticles_ChemicalFormulas(1, 'c77h120n18o26s');
```

La fórmula debe **empezar por una letra** (símbolo de elemento). Hay más ejemplos, incluidos casos de uso incorrecto, en `PL_SQL/Procedures/Subparticles_ChemicalFormulas_Ejemplos.sql`.

Para el ADN/ARN existe además `Subparticles_NitrogenousBases`, con su propio archivo de ejemplos.

---

## 📄 Licencia

Publicado bajo licencia **GNU GPL v3**. Puedes usarlo, estudiarlo, modificarlo y redistribuirlo; las obras derivadas deben mantener la misma licencia.

---

<p align="center">
  Hecho con ⚗️ y curiosidad por <strong>Alexei Barberà Roca</strong><br>
  <a href="https://www.linkedin.com/in/alexeibarberaroca">LinkedIn</a> ·
  <a href="https://github.com/alexeibarberaroca">GitHub</a> ·
  <a href="https://relativedevelopers.com/">Relative Developers</a>
</p>
