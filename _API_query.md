# API Query - Organización y método de consulta.

Para realizar consultas a un API desde un proyecto de React se recomienda llevar cierta estructura de carpetas y archivos para organizar de forma correcta el código.  

- Crear carpeta **"server"** o **"api"** dentro de **"src"** del proyecto para almacenar todo lo relacionado con las consultas.  

- Crear dentro de la carpeta destinada un archivo para almacenar la confuguración de la consulta a la API, puede ser nombrado **"config.js"** y podria contener por ejemplo la URL base:  

  ~~~javascript
    // api/config.js
    export const API_BASE_URL = 'https://api.example.com'
  ~~~  

- Crear archivos individuales para cada servicio necesario, los archivos contendran las funciones para realizar las consultas:  

  ~~~javascript
    // api/userService.js
    import { API_BASE_URL } from './config'

    export function getUsers() {
      return fetch(`${API_BASE_URL}/users`)
        .then(response => response.json())
    }

    // api/productService.js
    import { API_BASE_URL } from './config';

    export function getProducts() {
      return fetch(`${API_BASE_URL}/products`)
        .then(response => response.json());
    }
  ~~~  
- Importar los servicios y utilizar las funciones dentro de los componentes para obtener los datos de la API:  

  ~~~javascript
  import React, { useEffect, useState } from 'react';
  import { getUsers } from '../api/userService';

  function UserList() {
    const [users, setUsers] = useState([]);

    useEffect(() => {
      getUsers().then(data => setUsers(data));
    }, []);

    return (
      <div>
        <h1>User List</h1>
        {users.map(user => (
          <div key={user.id}>
            <p>Name: {user.name}</p>
            <p>Email: {user.email}</p>
          </div>
        ))}
      </div>
    );
  }

  export default UserList;
  ~~~
