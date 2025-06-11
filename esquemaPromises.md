```mermaid
graph TD
    A[Promise (Objeto)] --> B{Estado Interno};
    B --> B1[Pending (Pendiente)];
    B --> B2[Fulfilled (Cumplida / Resuelta)];
    B --> B3[Rejected (Rechazada)];

    A --> C[Constructor de Promise];
    C --> D(Parámetro: Función Ejecutora);
    D --> D1[Se ejecuta automáticamente al llamar al constructor];
    D --> D2[Generalmente inicia una operación asíncrona];
    D --> D3[Dicta cómo se debe ejecutar la promesa];
    D --> E(Parámetros de la Función Ejecutora);

    E --> E1[resolve() - Función];
    E1 --> E1a[Un solo argumento (valor resuelto)];
    E1a --> E1b[Invocarla cambia el estado de Pending a Fulfilled];
    E1b --> E1c[El valor resuelto de la promesa se establece en el argumento pasado a resolve()];
    E1 --> E1d[No definida por el programador];
    E1d --> E1e[JavaScript pasa su propia función resolve() al ejecutor];

    E --> E2[reject() - Función];
    E2 --> E2a[Toma una razón o un error como argumento];
    E2a --> E2b[Invocarla cambia el estado de Pending a Rejected];
    E2b --> E2c[El motivo del rechazo se establece en el argumento pasado a reject()];
    E2 --> E2d[No definida por el programador];
    E2d --> E2e[JavaScript pasa su propia función reject() al ejecutor];

    A --> F[Métodos para "Consumir" la Promesa];

    F --> F1[.then(onFulfilled, onRejected)];
    F1 --> F1a[onFulfilled (Callback de éxito)];
    F1a --> F1a1[Función que se ejecuta cuando la promesa es Fulfilled];
    F1a1 --> F1a2[Recibe el valor resuelto como argumento (ej: 'mensajeExito')];
    F1 --> F1b[onRejected (Callback de error - Opcional)];
    F1b --> F1b1[Función que se ejecuta cuando la promesa es Rejected];
    F1b1 --> F1b2[Recibe la razón del rechazo como argumento (ej: 'mensajeError')];
    F1 --> F1c[Retorna una nueva Promesa (para encadenamiento)];

    F --> F2[.catch(onRejected)];
    F2 --> F2a[Es una forma más concisa de .then(null, onRejected)];
    F2a --> F2a1[Función que se ejecuta cuando la promesa es Rejected];
    F2a1 --> F2a2[Recibe la razón del rechazo como argumento (ej: 'mensajeError')];
    F2 --> F2b[Retorna una nueva Promesa (para encadenamiento)];

    F --> F3[.finally(onFinally)];
    F3 --> F3a[Función que se ejecuta cuando la promesa es Fulfilled o Rejected (siempre)];
    F3a --> F3a1[No recibe ningún argumento];
    F3a --> F3a2[Útil para limpieza (ej: ocultar un spinner de carga)];
    F3 --> F3b[Retorna una nueva Promesa];
