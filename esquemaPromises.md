graph TD
    A[Promise &#40;Objeto&#41;] --> B{Estado Interno};
    B --> B1[Pending &#40;Pendiente&#41;];
    B --> B2[Fulfilled &#40;Cumplida &#47; Resuelta&#41;];
    B --> B3[Rejected &#40;Rechazada&#41;];

    A --> C[Constructor de Promise];
    C --> D(Parámetro: Función Ejecutora);
    D --> D1[Se ejecuta automáticamente al llamar al constructor];
    D --> D2[Generalmente inicia una operación asíncrona];
    D --> D3[Dicta cómo se debe ejecutar la promesa];
    D --> E(Parámetros de la Función Ejecutora);

    E --> E1[resolve&#40;&#41; - Función];
    E1 --> E1a[Un solo argumento &#40;valor resuelto&#41;];
    E1a --> E1b[Invocarla cambia el estado de Pending a Fulfilled];
    E1b --> E1c[El valor resuelto de la promesa se establece en el argumento pasado a resolve&#40;&#41;];
    E1 --> E1d[No definida por el programador];
    E1d --> E1e[JavaScript pasa su propia función resolve&#40;&#41; al ejecutor];

    E --> E2[reject&#40;&#41; - Función];
    E2 --> E2a[Toma una razón o un error como argumento];
    E2a --> E2b[Invocarla cambia el estado de Pending a Rejected];
    E2b --> E2c[El motivo del rechazo se establece en el argumento pasado a reject&#40;&#41;];
    E2 --> E2d[No definida por el programador];
    E2d --> E2e[JavaScript pasa su propia función reject&#40;&#41; al ejecutor];

    A --> F[Métodos para "Consumir" la Promesa];

    F --> F1[.then&#40;onFulfilled, onRejected&#41;];
    F1 --> F1a[onFulfilled &#40;Callback de éxito&#41;];
    F1a --> F1a1[Función que se ejecuta cuando la promesa es Fulfilled];
    F1a1 --> F1a2[Recibe el valor resuelto como argumento &#40;ej: 'mensajeExito'&#41;];
    F1 --> F1b[onRejected &#40;Callback de error - Opcional&#41;];
    F1b --> F1b1[Función que se ejecuta cuando la promesa es Rejected];
    F1b1 --> F1b2[Recibe la razón del rechazo como argumento &#40;ej: 'mensajeError'&#41;];
    F1 --> F1c[Retorna una nueva Promesa &#40;para encadenamiento&#41;];

    F --> F2[.catch&#40;onRejected&#41;];
    F2 --> F2a[Es una forma más concisa de .then&#40;null, onRejected&#41;];
    F2a --> F2a1[Función que se ejecuta cuando la promesa es Rejected];
    F2a1 --> F2a2[Recibe la razón del rechazo como argumento &#40;ej: 'mensajeError'&#41;];
    F2 --> F2b[Retorna una nueva Promesa &#40;para encadenamiento&#41;];

    F --> F3[.finally&#40;onFinally&#41;];
    F3 --> F3a[Función que se ejecuta cuando la promesa es Fulfilled o Rejected &#40;siempre&#41;];
    F3a --> F3a1[No recibe ningún argumento];
    F3a --> F3a2[Útil para limpieza &#40;ej: ocultar un spinner de carga&#41;];
    F3 --> F3b[Retorna una nueva Promesa];
