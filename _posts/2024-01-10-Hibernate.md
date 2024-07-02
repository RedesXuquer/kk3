---
title: Hibernate
date: 2024-01-10 12:00:00 +0100
categories: [Desarrollo Aplicaciones Multiplataforma, Acceso Datos]
tags: [acceso a datos, teoría, 2DAM]
img_path: /assets/img/hibernate/
---

# Hibernate
Con la siguiente estructura SQL:

```
CREATE DATABASE canciones;

CREATE TABLE `song` (
  `songId` int(11) NOT NULL,
  `songName` varchar(25) NOT NULL,
  `singer` varchar(25) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;
```

1. Añadimos las librerías, deben quedar de la siguiente manera:
![Alt text](<Captura de pantalla 2024-01-10 200549.png>)
![Alt text](<Captura de pantalla 2024-01-10 200537.png>)
![Alt text](<Captura de pantalla 2024-01-10 200802.png>)

1. Añadimos una clase con el siguiente contenido:
   
```
import javax.persistence.Column;
import javax.persistence.Entity;
import javax.persistence.Id;
import javax.persistence.Table;


@Entity
// Seleccionamos el nombre de la tabla
@Table(name = "song")
 
// POJO class
public class Song {

    // Indicamos el tipo ID y le marcamos el nombre de la columna, en este caso songId. Después le marcamos el tipo de dato, en este caso **int** y el nombre de la variable id.
    @Id @Column(name = "songId") private int id;

    // Indicamos el nombre de la segunda columna **songName**. Después le marcamos el tipo de dato, en este caso **String** y el nombre de la variable songName.
    @Column(name = "songName") private String songName;
 
    // Indicamos el nombre de la tercera columna **singer**. Después le marcamos el tipo de dato, en este caso **String** y el nombre de la variable artist.
    @Column(name = "singer") private String artist;
 
    // Método con el cual devolvemos el ID
    public int getId() { return id; }
 
    // Método con el cual establecemos el ID
    public void setId(int id) { this.id = id; }
 
    // Método con el cual devolvemos el nombre de la canción
    public String getSongName() { return songName; }

    // Método con el cual establecemos el nombre de la canción 
    public void setSongName(String songName)
    {
        this.songName = songName;
    }

    // Método con el cual devolvemos el nombre del artista
    public String getArtist() { return artist; }

    // Método con el cual establecemos el nombre del artista 
    public void setArtist(String artist)
    {
        this.artist = artist;
    }
}
```

1. Los import:
   
```
import java.util.HashSet;
import java.util.List;
import java.util.Set;
import org.hibernate.Session;
import org.hibernate.SessionFactory;
import org.hibernate.cfg.Configuration;
```

1. Trabajando con las sesiones:

```
    void crearSession(){

        // Paso 1: Crear una instancia de la clase Configuration
        Configuration configuration = new Configuration();

        // Paso 2: Configurar Hibernate cargando la configuración desde "hibernate.cfg.xml"
        configuration.configure("hibernate.cfg.xml");

        // Paso 3: Agregar la clase Song como una clase anotada en la configuración de Hibernate
        configuration.addAnnotatedClass(Song.class);
        
        // Paso 4: Construir la fábrica de sesiones (SessionFactory) utilizando la configuración
        this.sessionFactory = configuration.buildSessionFactory();
    }
```

1. CRUD

Create

```
void crearCancion(String songName, String artist) {
    // Intenta abrir una sesión utilizando la fábrica de sesiones existente
    try (Session session = this.sessionFactory.openSession()) {
        // Inicia una transacción en la sesión
        session.beginTransaction();

        // Crea una nueva instancia de la clase Song y establece sus propiedades
        Song nuevo = new Song();
        nuevo.setSongName(songName);
        nuevo.setArtist(artist);

        // Guarda la nueva instancia de Song en la base de datos
        session.save(nuevo);

        // Realiza commit para confirmar la transacción
        session.getTransaction().commit();

        // Cierra la sesión después de completar las operaciones
        session.close();
    }
}
```

Read

```
void crearCancion(String songName, String artist) {
    // Intenta abrir una sesión utilizando la fábrica de sesiones existente
    try (Session session = this.sessionFactory.openSession()) {
        // Inicia una transacción en la sesión
        session.beginTransaction();

        // Crea una nueva instancia de la clase Song
        Song nuevo = new Song();

        // Establece el nombre de la canción y el artista en la instancia de Song
        nuevo.setSongName(songName);
        nuevo.setArtist(artist);

        // Guarda la nueva instancia de Song en la base de datos
        session.save(nuevo);

        // Realiza commit para confirmar la transacción
        session.getTransaction().commit();

        // Cierra la sesión después de completar las operaciones
        session.close();
    }
}
```

Update

```
void actualizarProducto(int id, String songName, String artist) {
    // Intenta abrir una sesión utilizando la fábrica de sesiones existente
    try (Session session = this.sessionFactory.openSession()) {
        // Inicia una transacción en la sesión
        session.beginTransaction();

        // Obtén el objeto Song de la base de datos con el id proporcionado
        Song cancion = session.get(Song.class, id);

        // Actualiza los campos si se encuentra el objeto Song
        if (cancion != null) {
            // Establece el nuevo nombre de la canción y artista
            cancion.setSongName(songName);
            cancion.setArtist(artist);
        }

        // Realiza commit para confirmar la transacción
        session.getTransaction().commit();

        // Cierra la sesión después de completar las operaciones
        session.close();
    }
}
```

Delete

```
void eliminarProducto(int id) {
    // Intenta abrir una sesión utilizando la fábrica de sesiones existente
    try (Session session = this.sessionFactory.openSession()) {
        // Inicia una transacción en la sesión
        session.beginTransaction();

        // Obtén el objeto Song de la base de datos con el id proporcionado
        Song cancion = session.get(Song.class, id);

        // Elimina el objeto Song si se encuentra
        if (cancion != null) {
            // Utiliza el método delete para eliminar la instancia de Song de la base de datos
            session.delete(cancion);
        }

        // Realiza commit para confirmar la transacción
        session.getTransaction().commit();

        // Cierra la sesión después de completar las operaciones
        session.close();
    }
}
```

Para finalizar la sesión:

```
void cerrar() {
    // Cierra la fábrica de sesiones
    this.sessionFactory.close();
}
```

1. Añadimos un archivo XML dento de nuestro proyecto, se debe llamar **hibernate.cfg.xml* con el siguiente contenido:
```
<?xml version = "1.0" encoding = "utf-8"?>
<!DOCTYPE hibernate-configuration PUBLIC
        "-//Hibernate/Hibernate Configuration DTD 3.0//EN"
        "http://www.hibernate.org/dtd/hibernate-configuration-3.0.dtd">
<hibernate-configuration>
    <session-factory>
        <property name = "hibernate.connection.driver_class">com.mysql.jdbc.Driver</property>
        <!-- Set URL -->
        <property name = "hibernate.connection.url">jdbc:mysql://localhost:3306/canciones</property>
        //<property name = "hibernate.connection.url">jdbc:mysql://**direccion_server**:**puerto**/**nombre_BBDD**</property>
        <!-- Set User Name -->
        <property name = "hibernate.connection.username">2DAM</property>
        //<property name = "hibernate.connection.username">**User_BBDD**</property>
        <!-- Set Password -->
        <property name = "hibernate.connection.password">2DAM2023</property>
        //<property name = "hibernate.connection.password">**Pass_BBDD**</property>
        <!-- Set Driver Name -->
        <property name = "hibernate.show_sql">true</property>
        
    </session-factory>
</hibernate-configuration>
```

Esto es todo.